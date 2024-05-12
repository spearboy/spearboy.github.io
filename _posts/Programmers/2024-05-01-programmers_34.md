---
layout: post
title: 프로그래머스 LV1 "같은 숫자는 싫어"
date: 2024-05-01 21:51 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv1 같은 숫자는 싫어

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 열네번째 문제 '같은 숫자는 싫어' 문제입니다.

  ![프로그래머스 이미지](https://spearboy.github.io/assets/img/같은숫자는싫어_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 `arr`이라는 정수가 담겨있는 배열이 주어지면 `arr`안에 있는 요소중 연속으로 나오는 정수는 1개만 남겨 다시 배열의 형태로 출력하는 문제입니다.

  오늘 문제에서는 간단한 반복문과 조건문, 그리고 배열 메서드로 문제를 해결해 보겠습니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(arr)
{
  var answer = [];
  
  return answer;
}
```

기본 세팅 코드는 간단하게 `arr`이라는 배열의 매개변수를 전달하며 함수 내에 `answer`배열을 선언해 리턴하는 기본적인 함수의 형태입니다.

우선, 문제를 해결하기 위해 반복문과 조건문, 그리고 배열 메서드를 사용하는 방법을 살펴볼까요?

우선 반복문을 사용하여 배열을 순회합니다. 그리고 현재 원소와 그 다음 원소를 비교하여 중복된 숫자를 걸러내면 됩니다. 이때, 중복을 걸러내기 위해 조건문을 사용합니다.

그리고 중복된 숫자를 걸러내는 방법 중 하나로 배열 메서드인 `filter`를 사용할 수도 있습니다. `filter` 메서드를 사용하면 조건에 맞는 원소만 걸러낼 수 있습니다. 이를 통해 중복된 숫자를 제거할 수 있습니다.

우선 `filter`가 무엇인지 한번 알아보고 문제를 이어서 풀어보겠습니다.

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

이렇게 `filter`에 대해 한번 알아 보았습니다. 그럼 이제 예를 들어, 배열 [1, 1, 2, 2, 3, 3, 3, 4, 4, 5]를 사용하여 문제를 해결하는 방법에 대해 설명해보겠습니다.

1. 반복문과 조건문 사용:

```javascript
function solution(arr) {
  var answer = [];

  for (let i = 0; i < arr.length; i++) {
    // 현재 원소와 다음 원소가 다를 때만 answer 배열에 추가
    if (arr[i] !== arr[i + 1]) {
      answer.push(arr[i]);
    }
  }
  
  return answer;
}
console.log(solution([1, 1, 2, 2, 3, 3, 3, 4, 4, 5])); // [1, 2, 3, 4, 5]
```

2. `filter` 메서드 사용:

```javascript
function solution(arr) {
  // 배열에서 중복된 숫자를 걸러내고, 현재 원소와 다음 원소가 다를 때만 필터링
  return arr.filter((value, index) => value !== arr[index + 1]);
}
console.log(solution([1, 1, 2, 2, 3, 3, 3, 4, 4, 5])); // [1, 2, 3, 4, 5]
```

이렇게 반복문과 조건문, 그리고 배열 메서드를 사용하여 중복된 숫자를 걸러내는 방법을 설명해보았습니다. 이를 통해 문제를 해결할 수 있습니다.

그럼 정리된 코드를 한번 작성해보겠습니다.

```javascript
function solution(arr)
{
    var answer = [];

    for (let i = 0; i < arr.length; i++) {
        if (arr[i] !== arr[i + 1]) {
            answer.push(arr[i]);
        }
    }
    
    return answer;
}
```

문제의 식이 완성되었으니 프로그래머스에 한번 확인해보겠습니다.

![프로그래머스 이미지](https://spearboy.github.io/assets/img/같은숫자는싫어_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '같은 숫자는 싫어' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.