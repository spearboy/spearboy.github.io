---
layout: post
title: 프로그래머스 LV2 "모음 사전"
date: 2024-06-14 18:13 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 모음 사전

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '모음 사전' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 단어 `word`가 모음 사전에서 몇 번째 단어인지 찾는 것입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(word) {
    var answer = 0;
    return answer;
}
```

기본 세팅 코드는 매개변수 `word`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `순열`과 `조합`을 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. 모음 사전을 생성합니다.
2. 주어진 단어 `word`가 모음 사전에서 몇 번째인지 찾습니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(word) {
    const vowels = ['A', 'E', 'I', 'O', 'U'];
    const dictionary = [];
    
    function generateWords(current) {
        if (current.length > 5) return;
        if (current) dictionary.push(current);
        for (const vowel of vowels) {
            generateWords(current + vowel);
        }
    }
    
    generateWords('');
    
    dictionary.sort();
    
    return dictionary.indexOf(word) + 1;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `const vowels = ['A', 'E', 'I', 'O', 'U'];`: 모음 리스트를 선언합니다.
2. `const dictionary = [];`: 모음 사전을 저장할 배열을 선언합니다.
3. `function generateWords(current) { ... }`: 재귀적으로 모음 사전을 생성하는 함수입니다.
4. `if (current.length > 5) return;`: 단어의 길이가 5를 초과하면 종료합니다.
5. `if (current) dictionary.push(current);`: 현재 단어를 사전에 추가합니다.
6. `for (const vowel of vowels) { generateWords(current + vowel); }`: 각 모음을 현재 단어에 추가하여 재귀 호출합니다.
7. `generateWords('');`: 초기 호출로 빈 문자열을 사용하여 모음 사전을 생성합니다.
8. `dictionary.sort();`: 사전을 정렬합니다.
9. `return dictionary.indexOf(word) + 1;`: 주어진 단어의 인덱스를 찾아 1을 더하여 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '모음 사전' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
