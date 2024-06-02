---
layout: post
title: 프로그래머스 LV2 "영어 끝말잇기"
date: 2024-05-22 21:28 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 영어 끝말잇기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '영어 끝말잇기' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post49_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 `n`과 단어를 담은 리스트 `words`가 주어집니다. 가장 먼저 탈락하는 사람의 번호와 그 사람이 자신의 몇 번째 차례에 탈락하는지를 찾아 배열의 형태로 출력하는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(n, words) {
  var answer = [];
  console.log('Hello Javascript')
  return answer;
}
```

기본 세팅 코드는 매개변수 `n`과 `words`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

오늘 문제의 핵심을 간단하게 문제를 풀어보면

1. 끝말잇기 규칙 확인

2. 이전 단어 사용 여부 체크

3. 규칙 어긴 사람의 번호와 차례 찾기

위 순서가 오늘 문제의 핵심입니다.

그전에 오늘 사용해볼 `Set 객체 메서드` 를 잠시 알아보고 문제를 풀어보겠습니다.

# Set 객체 메서드 설명

`Set`은 중복을 허용하지 않고 순서가 없는 데이터 집합을 나타내는 자료형입니다. 다양한 메서드를 사용하여 `Set` 객체를 조작할 수 있습니다. 여기에는 몇 가지 주요 메서드가 있습니다:

- `add(element)`: `Set`에 원소를 추가합니다. 이미 존재하는 원소를 추가하려고 하면 아무런 작업을 하지 않습니다.

- `remove(element)`: `Set`에서 주어진 원소를 제거합니다. 해당 원소가 존재하지 않으면 `KeyError`가 발생합니다.

- `discard(element)`: `Set`에서 주어진 원소를 제거합니다. 해당 원소가 존재하지 않아도 오류를 발생시키지 않습니다.

- `clear()`: `Set`의 모든 원소를 제거합니다.

- `copy()`: `Set`의 얕은 복사본을 반환합니다.

- `union(other_set)`: 두 `Set`을 합친 새로운 `Set`을 반환합니다.

- `intersection(other_set)`: 두 `Set`의 교집합을 반환합니다.

- `difference(other_set)`: 한 `Set`에는 있지만 다른 `Set`에는 없는 원소들로 이루어진 새로운 `Set`을 반환합니다.

- `symmetric_difference(other_set)`: 두 `Set`의 대칭 차집합을 반환합니다.

- `issubset(other_set)`: 현재 `Set`이 다른 `Set`의 부분집합인지 확인합니다.

- `issuperset(other_set)`: 현재 `Set`이 다른 `Set`의 상위집합인지 확인합니다.

- `pop()`: `Set`에서 임의의 원소를 제거하고 반환합니다. 만약 `Set`이 비어있으면 `KeyError`가 발생합니다.

이러한 메서드를 사용하여 `Set` 객체를 조작할 수 있습니다.

그럼 오늘 문제의 풀이를 코드로 한번 작성해 보겠습니다.

```javascript
function solution(n, words) {
  let usedWords = new Set();
  usedWords.add(words[0]);

  for (let i = 1; i < words.length; i++) {
    let currentWord = words[i];
    let previousWord = words[i - 1];
    if (currentWord[0] !== previousWord[previousWord.length - 1]) {
      let person = (i % n) + 1;
      let turn = Math.floor(i / n) + 1;
      return [person, turn];
    }
    if (usedWords.has(currentWord)) {
      let person = (i % n) + 1;
      let turn = Math.floor(i / n) + 1;
      return [person, turn];
    }
    usedWords.add(currentWord);
  }
  return [0, 0];
}
```
위 코드의 간단한 설명을 알려드리겠습니다.

1. `usedWords`라는 `Set` 객체를 사용하여 이미 사용된 단어를 저장합니다.
- `Set`은 중복된 값을 허용하지 않으므로 이미 사용된 단어인지 효율적으로 확인할 수 있습니다.
- 첫 번째 단어는 항상 사용되므로 처음에 `Set`에 추가합니다.

2. 단어 순회 및 규칙 확인:
- `for` 루프를 사용하여 두 번째 단어부터 마지막 단어까지 차례대로 검사합니다.
- 각 반복마다 `currentWord`와 `previousWord`를 설정합니다.

3. 규칙 1: 앞 단어의 마지막 문자로 시작하는지 확인:
- `currentWord[0]`와 `previousWord[previousWord.length - 1]`를 비교하여 규칙을 어겼는지 확인합니다.
- 규칙을 어겼다면, 해당 단어를 말한 사람의 번호와 차례를 계산하여 반환합니다.
- `person = (i % n) + 1`은 사람의 번호를 계산합니다.
- `turn = Math.floor(i / n) + 1`은 몇 번째 차례인지를 계산합니다.

4. 규칙 2: 이미 등장했던 단어인지 확인:
- `usedWords.has(currentWord)`로 이미 사용된 단어인지 확인합니다.
- 이미 사용된 단어라면, 해당 단어를 말한 사람의 번호와 차례를 계산하여 반환합니다.

5. 단어 사용 기록 업데이트:
- `usedWords.add(currentWord)`를 사용하여 현재 단어를 사용된 단어 목록에 추가합니다.

6. 모든 단어가 규칙을 어기지 않았을 경우:
- `for` 루프가 끝날 때까지 규칙을 어긴 단어가 없다면 `[0, 0]`을 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.


![프로그래머스 이미지](/assets/img/post49_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '영어 끝말잇기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.