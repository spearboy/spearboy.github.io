---
layout: post
title: 프로그래머스 LV2 "없는 숫자 더하기"
date: 2024-05-29 16:46 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV1 없는 숫자 더하기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 문제 '없는 숫자 더하기' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post57_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 배열인 `numbers`가 주어집니다. `numbers`배열안에서 찾을 수 없는 0~9까지의 모든 숫자를 더해 출력하는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(numbers) {
  var answer = -1;
  return answer;
}
```

기본 세팅 코드는 매개변수 `numbers`이 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

오늘 문제의 핵심을 간단하게 문제를 풀어보면

1. 주어진 배열에서 없는 숫자를 모두 찾기

2. 찾은 모든 숫자를 더한값을 출력한다.

위 순서가 오늘 문제의 핵심입니다.

오늘 사용할 메서드인 `filter`는 이전 포스팅에서 한번 소개해드렸지만 오늘 다시 한번 복습해보고 문제를 이어서 풀어보겠습니다.


## filter

`filter` 메서드는 배열에서 원하는 조건을 만족하는 요소만 걸러내어 새로운 배열을 반환하는 메서드입니다. 이 메서드는 매우 유용하며, 코드를 더 간결하고 가독성 있게 만들어줍니다.

`filter` 메서드는 다음과 같이 사용합니다:

```javascript
const newArray = array.filter(callback(element, index, array));
```

여기서,

+ `array`: 필터링할 원본 배열입니다.
+ `callback`: 각 요소에 대해 실행할 함수로, 세 가지 매개변수를 받습니다.
  + `element`: 배열의 현재 요소입니다.
  + `index` (선택사항): 배열의 현재 요소의 인덱스입니다.
  + `array` (선택사항): 원본 배열 자체입니다.
  + `callback` 함수는 `true`를 반환하는 요소만 새로운 배열에 포함시킵니다. 반환값이 `true`인 경우에만 해당 요소가 유지되고, 그렇지 않은 경우는 필터링됩니다.

이제 이를 예시로 설명해보겠습니다.

```javascript
const numbers = [1, 2, 3, 4, 5];

// 짝수만 필터링하여 새로운 배열 생성
const evenNumbers = numbers.filter(num => num % 2 === 0);

console.log(evenNumbers); // [2, 4]
```

위 예제에서는 `filter` 메서드를 사용하여 `numbers` 배열에서 짝수만 걸러내어 `evenNumbers` 배열에 저장합니다. 이때, 화살표 함수를 사용하여 각 요소를 판별하는 조건을 지정했습니다. 이 조건은 해당 숫자가 2로 나누어 떨어지는지 확인하여 짝수인지를 판별합니다.

이렇게 `filter` 메서드를 사용하면 원하는 조건에 맞는 요소만을 간단하게 추출할 수 있습니다.

이렇게 `filter`에 대해 한번 알아 보았습니다.

그럼 오늘 문제의 풀이를 코드로 한번 작성해 보겠습니다.

```javascript
function solution(numbers) {
  var answer = -1;
  const allNumbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
  const missingNumbers = allNumbers.filter(num => !numbers.includes(num));
  answer = missingNumbers.reduce((sum, num) => sum + num, 0);
  
  return answer;
}
```
위 코드의 간단한 설명을 알려드리겠습니다.

1. 초기화:
- answer라는 변수를 -1로 초기화합니다. 이 변수는 나중에 최종 결과를 저장하는 데 사용됩니다.

2. 모든 숫자 배열 생성:
- 0부터 9까지의 숫자를 포함하는 배열 allNumbers를 만듭니다. 이 배열은 0부터 9까지의 모든 숫자를 포함하고 있습니다.

3. 누락된 숫자 필터링:
- allNumbers 배열에서 numbers 배열에 포함되지 않은 숫자들만 골라냅니다. 이를 위해 filter 메서드를 사용하여 numbers 배열에 없는 숫자들만 추출합니다.

4. 누락된 숫자들의 합 계산:
- 누락된 숫자들을 모아 놓은 배열 missingNumbers에서 모든 숫자들의 합을 계산합니다. 이를 위해 reduce 메서드를 사용합니다. 이 메서드는 배열의 각 요소를 순회하며 합을 누적합니다.

5. 결과 반환:
- 계산된 합을 answer 변수에 저장하고, 이를 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.


![프로그래머스 이미지](/assets/img/post57_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '없는 숫자 더하기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.