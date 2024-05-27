---
layout: post
title: 프로그래머스 LV2 "JadenCase 문자열 만들기"
date: 2024-05-15 23:03 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv2 JadenCase 문자열 만들기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 세번째 문제 'JadenCase 문자열 만들기' 문제입니다.

  ![프로그래머스 이미지](/assets/img//post43_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수 `s`라는 문자열이 주어지면 각 문자열 단어의 첫글자를 대문자로 변경하고 나머지는 소문자로 변경해 출력하는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(s) {
  var answer = '';
  return answer;
}
```

기본 세팅 코드는 매개변수 `s`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

우선 첫번째 로 `JadenCase`가 무엇인지 짧게 알아보고 다시 진행해보겠습니다.

## JadenCase 

JadenCase는 모든 단어의 첫 문자가 대문자이고, 나머지 문자가 소문자인 문자열 형식을 의미합니다. 이 형식에서는 첫 문자가 알파벳이 아닌 경우에도 나머지 문자는 소문자로 작성됩니다. 예를 들어:

- "hello world"는 JadenCase로 "Hello World"가 됩니다.
- "3people unFollowed me"는 JadenCase로 "3people Unfollowed Me"가 됩니다.

간단히 말해, JadenCase는 각 단어의 첫 글자를 대문자로 만들고 나머지 글자는 소문자로 만드는 형식입니다.

`JadenCase`가 무엇인지 저는 오늘 처음 알았습니다ㅎㅎ.. 제 짧은 설명 말고 알고계신게 있다면 댓글로 남겨주세요.

그리고 저희는 오늘 `map()`과 `.toLowerCase()`,`.toUpperCase()`가 무엇인지 한번 알아보고 문제풀이를 진행해보겠습니다.

## map()

`map` 메서드는 배열의 각 요소에 대해 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환합니다. 원본 배열은 변경되지 않습니다.

```javascript
array.map(callback(element, index, array), thisArg);
```

- `callback`: 각 배열 요소에 대해 실행할 함수. 세 가지 인수를 받을 수 있습니다:
  - `element`: 처리할 현재 요소.
  - `index`: 처리할 현재 요소의 인덱스.
  - `array`: `map`을 호출한 배열.
- `thisArg` (선택사항): `callback` 실행 시 `this`로 사용할 값.

### 배열의 각 요소를 제곱하기

```javascript
const numbers = [1, 2, 3, 4, 5];
const squaredNumbers = numbers.map(function(num) {
    return num * num;
});

console.log(squaredNumbers);  // [1, 4, 9, 16, 25]
```

또는 화살표 함수를 사용하여 더 간결하게 작성할 수 있습니다:

```javascript
const numbers = [1, 2, 3, 4, 5];
const squaredNumbers = numbers.map(num => num * num);

console.log(squaredNumbers);  // [1, 4, 9, 16, 25]
```

### 데이터 변환

각 객체에서 전체 이름을 생성하는 예제입니다.

```javascript
const users = [
    { firstName: 'John', lastName: 'Doe' },
    { firstName: 'Jane', lastName: 'Doe' },
    { firstName: 'Mary', lastName: 'Smith' }
];

const fullNames = users.map(user => `${user.firstName} ${user.lastName}`);

console.log(fullNames);  // ['John Doe', 'Jane Doe', 'Mary Smith']
```

### 객체 배열에서 특정 속성 추출

제품 배열에서 각 제품의 이름을 추출하는 예제입니다.

```javascript
const products = [
    { name: 'Laptop', price: 1000 },
    { name: 'Phone', price: 500 },
    { name: 'Tablet', price: 750 }
];

const productNames = products.map(product => product.name);

console.log(productNames);  // ['Laptop', 'Phone', 'Tablet']
```

### `map` 메서드의 특징

1. **새로운 배열 반환**: `map` 메서드는 원본 배열을 변경하지 않고, 새로운 배열을 반환합니다.
2. **콜백 함수**: 각 요소에 대해 호출되는 함수는 세 가지 인수를 받을 수 있습니다: 현재 요소, 현재 요소의 인덱스, 그리고 호출된 배열 자체.
3. **불변성**: 원본 배열은 그대로 유지되며, 결과는 새로운 배열에 저장됩니다.

`map` 메서드는 배열의 각 요소에 동일한 처리를 적용하여 새로운 배열을 생성할 때 매우 유용합니다.

## .toLowerCase()

`.toLowerCase()` 메서드는 문자열 객체에서 사용 가능한 메서드로, 문자열의 모든 문자를 소문자로 변환하여 새로운 문자열을 반환합니다. 이 메서드는 원본 문자열을 변경하지 않습니다.

- 역할: 문자열의 모든 문자를 소문자로 변환합니다.
- 사용법: `문자열.toLowerCase()`

### 예제

```javascript
let str = "Hello World!";
let lowerStr = str.toLowerCase();
console.log(lowerStr); // "hello world!"
```

### 특징

1. 원본 문자열 변경 없음: 원본 문자열은 그대로 유지됩니다.
2. 대문자만 소문자로 변환: 대문자 A-Z를 소문자 a-z로 변환합니다.

### 사용 사례

- 대소문자 무시 비교: 사용자 입력을 대소문자 구분 없이 비교할 때
- 데이터 표준화: 다양한 형식의 문자열을 소문자로 통일할 때
- 검색: 대소문자 구분 없이 문자열을 검색할 때

```javascript
// 사용자 입력 비교
let userInput = "HeLLo";
if (userInput.toLowerCase() === "hello") {
  console.log("입력이 'hello'입니다.");
}
```

`.toLowerCase()`는 문자열을 소문자로 변환하는 간단하고 유용한 메서드입니다.

## .toUpperCase()

`.toUpperCase()` 메서드는 문자열 객체에서 사용 가능한 메서드로, 문자열의 모든 문자를 대문자로 변환하여 새로운 문자열을 반환합니다. 이 메서드는 원본 문자열을 변경하지 않습니다.

- 역할: 문자열의 모든 문자를 대문자로 변환합니다.
- 사용법: `문자열.toUpperCase()`

### 예제

```javascript
let str = "Hello World!";
let upperStr = str.toUpperCase();
console.log(upperStr); // "HELLO WORLD!"
```

### 특징

1. 원본 문자열 변경 없음: 원본 문자열은 그대로 유지됩니다.
2. 소문자만 대문자로 변환: 소문자 a-z를 대문자 A-Z로 변환합니다.

### 사용 사례

- 대소문자 무시 비교: 사용자 입력을 대소문자 구분 없이 비교할 때
- 데이터 표준화: 다양한 형식의 문자열을 대문자로 통일할 때
- 검색: 대소문자 구분 없이 문자열을 검색할 때

```javascript
// 사용자 입력 비교
let userInput = "HeLLo";
if (userInput.toUpperCase() === "HELLO") {
    console.log("입력이 'HELLO'입니다.");
}
```

`.toUpperCase()`는 문자열을 대문자로 변환하는 간단하고 유용한 메서드입니다.



이렇게 `map`,`.toLowerCase()`,`.toUpperCase()`가 무엇인지 한번 알아보았습니다.

그럼 코드의 결과를 한번 작성해 보겠습니다.

```javascript
function solution(s) {
  var answer = '';
  var array = s.split(" ");
  var word = array.map(e => {
    if (e.length > 0) {
      return e[0].toUpperCase() + e.slice(1).toLowerCase();
    } else {
      return e;
    }
  });
  answer = word.join(" ");
  return answer;
}
```
문제의 코드가 작성되었으니 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img//post43_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 'JadenCase 문자열 만들기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.