---
layout: post
title: 프로그래머스 LV1 "서울에서 김서방 찾기"
date: 2024-04-28 19:51 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv1 서울에서 김서방 찾기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 열한번째 문제 '서울에서 김서방 찾기' 문제입니다.

  ![프로그래머스 이미지](https://spearboy.github.io/assets/img/서울에서김서방찾기_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 `seoul`라는 배열이 주어지면 해당 배열안에 특정 요소를 찾아 문자열로 출력하는 문제입니다.

  오늘 문제에서는 간단한 반복문과 조건문으로 문제를 해결해 보겠습니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(seoul) {
  var answer = '';
  return answer;
}
```

기본 세팅 코드는 간단하게 `seoul`라는 배열형태의 매개변수를 전달하며 함수 내에 `answer`변수를 선언해 리턴하는 기본적인 함수의 형태입니다.

이 기본 함수에 이번 문제의 핵심인 "Kim"이라는 요소가 몇번째 `index`에 있는지 찾은 후 해당 `index`값과 문자열을 합쳐 리턴하는것입니다.

여기서 잠시 이전에도 설명 드렸지만 왜 배열의 반복에서는 `forEach`를 사용하는지 한번 알아보고 넘어가겠습니다.

### forEach()
`forEach()` 메서드는 배열의 각 요소에 대해 제공된 함수를 한 번씩 실행하는 배열 메서드입니다. 이를 사용하는 이유는 다음과 같습니다.
  1. 가독성과 간결성: `forEach()`는 코드를 간결하고 읽기 쉽게 만듭니다. `for` 루프를 사용하는 대신 `forEach()`를 사용하면 코드가 더 짧아지고 더 명확해집니다.
```javascript
// for 루프를 사용한 예시
const numbers = [1, 2, 3, 4, 5];
for (let i = 0; i < numbers.length; i++) {
  console.log(numbers[i]);
}

// forEach()를 사용한 예시
const numbers = [1, 2, 3, 4, 5];
numbers.forEach(function(number) {
  console.log(number);
});
```
  2. 배열 요소에 대한 반복 작업: `forEach()`를 사용하면 배열의 각 요소에 대해 반복 작업을 수행할 수 있습니다. 이는 배열을 반복하면서 각 요소에 대해 동일한 작업을 수행해야 할 때 매우 유용합니다.
```javascript
const numbers = [1, 2, 3, 4, 5];
numbers.forEach(function(number) {
  console.log(number * 2); // 각 요소를 2배로 곱하여 출력
});
```
  3. 인라인 함수 사용: `forEach()`를 사용하면 인라인 함수를 쉽게 작성할 수 있습니다. 인라인 함수를 사용하면 반복 작업을 보다 간단하게 처리할 수 있습니다.
```javascript
const numbers = [1, 2, 3, 4, 5];
numbers.forEach(number => console.log(number * 2)); // 화살표 함수를 사용하여 인라인 함수 작성
```
  4. 콜백 함수 사용: `forEach()`의 인자로 전달되는 콜백 함수는 각 배열 요소에 대해 실행됩니다. 이는 `forEach()`를 사용하여 다양한 작업을 수행할 수 있다는 것을 의미합니다.
```javascript
const numbers = [1, 2, 3, 4, 5];
numbers.forEach(function(number, index, array) {
  console.log(`Index: ${index}, Value: ${number}`); // 각 요소와 해당 인덱스 출력
});
```
  5. 배열 변경 및 사이드 이펙트: `forEach()`를 사용하면 배열을 변경할 수 있으며, 이는 `map()`과는 다릅니다. 만약 단순히 배열의 요소를 반복하면서 작업을 수행하고자 할 때라면 `forEach()`가 적합한 선택입니다.
```javascript
const numbers = [1, 2, 3, 4, 5];
const doubledNumbers = [];
numbers.forEach(function(number) {
  doubledNumbers.push(number * 2); // 각 요소를 2배로 곱하여 새 배열에 추가
});
console.log(doubledNumbers); // [2, 4, 6, 8, 10]
```

이렇게 `forEach`에 대해 한번 알아봤습니다. 위에서 말한것과 같이 저는 주로 1번의 이유때문에 `forEach`를 사용합니다.
하지만 오늘은 4번의 이유인 `forEach`의 콜백함수를 사용하기 위해 `forEach`를 사용하겠습니다.

또 한가지 콜백함수가 무엇인지 한번 간단하게 설명드리고 다시 문제를 풀어보겠습니다.

### 콜백함수

콜백 함수는 다른 함수에 인수로 전달되는 함수를 말합니다. 이 콜백 함수는 주로 비동기적인 작업을 처리하거나 다른 함수의 동작을 완료한 후에 호출되는데 사용됩니다.

간단한 예제를 통해 설명하겠습니다. 아래 코드에서 forEach 메서드는 배열의 각 요소에 대해 주어진 함수를 실행합니다. 이때 주어진 함수가 콜백 함수입니다.

```javascript
const numbers = [1, 2, 3, 4, 5];

numbers.forEach(function(number) {
  console.log(number);
});
```

여기서 forEach 메서드에 전달된 함수가 콜백 함수입니다. 이 콜백 함수는 배열 numbers의 각 요소를 처리하고 있습니다. 즉, forEach 메서드는 배열의 요소를 반복하면서 콜백 함수를 호출합니다.

또 다른 예로, 비동기적인 작업을 처리하는 경우도 있습니다. 예를 들어, setTimeout 함수는 일정 시간이 지난 후에 주어진 함수를 실행하는데, 이때 주어진 함수가 콜백 함수입니다.

```javascript
setTimeout(function() {
  console.log('Hello, world!');
}, 1000); // 1초 후에 'Hello, world!'를 출력
```

이 경우에도 setTimeout 함수에 전달된 함수가 콜백 함수입니다. 이 함수는 1초 후에 실행됩니다.

요약하자면, 콜백 함수는 다른 함수에 인수로 전달되어 그 함수의 동작이 완료된 후에 호출되는 함수입니다. 이를 통해 비동기적인 작업을 처리하거나 다른 함수의 동작을 확장할 수 있습니다.

이렇게 콜백함수가 무엇인지 간단하게 설명 드렸습니다.

그럼 다시 문제를 해결해 보겠습니다.

```javascript
function solution(seoul) {
  var answer = '';
  seoul.forEach(function(e,index){
    if(e == "Kim"){
      answer = "김서방은 "+index+"에 있다";
    }
  })
  return answer;
}
```
위 코드와 같이 작성을 해주었습니다.
보시는 바와 같이 조건문에 해당 루프의 `e`, 즉 요소가 "Kim" 이라면 `answer`변수에 "김서방은 "+index+"에 있다" 라는 문자열을 담아주어 리턴해주는것입니다.

이렇게 문제의 식이 완성 되었습니다. 완성된 코드를 다시 한번 보여드리겠습니다.

```javascript
function solution(seoul) {
  var answer = '';
  seoul.forEach(function(e,index){
    if(e == "Kim"){
      answer = "김서방은 "+index+"에 있다";
    }
  })
  return answer;
}
```

문제의 식이 완성되었으니 프로그래머스에 한번 확인해보겠습니다.

![프로그래머스 이미지](https://spearboy.github.io/assets/img/서울에서김서방찾기_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '서울에서 김서방 찾기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.