---
layout: post
title: 프로그래머스 LV1 "자릿수 더하기"
date: 2024-04-21 15:43 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv1 자릿수 더하기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 네번째 문제 '자릿수 더하기' 문제입니다.

  ![프로그래머스 이미지](/assets/img/자릿수더하기_01.jpg)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 정수 `n`이 주어지면 `n`의 각 자릿수를 구해서 전부 더한값을 출력하면 되는 간단한 문제입니다.

  오늘 문제에서는 간단한 반복문과 이전 포스팅에서 사용했던 `Number()`내장함수와 `String()`내장함수를 사용해보겠습니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(n){
    var answer = 0;
    return answer;
}
```

기본 세팅코드는 간단하게 `n`라는 매개변수를 전달하며 함수내에 `answer`변수를 선언해 리턴하는 기본적인 함수의 형태입니다.

오늘은 문제를 풀기전에 `String()`내장함수에 대해 한번 알아보고 문제를 해결해 보겠습니다.   
`Number()`내장함수는 이전 포스팅인 [프로그래머스 Lv1 문자열을 정수로 바꾸기](https://spearboy.github.io/posts/programmers_22/)포스팅에서 확인 가능합니다.

그럼 `String()`내장함수에 대해 한번 알아보겠습니다.

### String()

  `String()` 함수는 주어진 값을 문자열로 변환하는 JavaScript의 내장 함수입니다. 이 함수는 다양한 데이터 형식을 문자열로 변환할 수 있습니다.

  + 숫자를 문자열로 변환하기: 숫자를 문자열로 변환할 때는 다음과 같이 사용합니다.
    + ```javascript
      let num = 123;
      let str_num = String(num); // 숫자를 문자열로 변환
      console.log(str_num); // 출력: "123"
      ```

  + `boolean`을 문자열로 변환하기: `boolean` 값을 문자열로 변환할 때는 다음과 같이 사용합니다.
    + ```javascript
      let bool = true;
      let str_bool = String(bool); // `boolean`을 문자열로 변환
      console.log(str_bool); // 출력: "true"
      ```

  + 객체를 문자열로 변환하기: 객체를 문자열로 변환할 때는 해당 객체를 그대로 문자열로 변환합니다. 주로 디버깅이나 로깅에서 사용될 수 있습니다.
    + ```javascript
      let obj = { name: "John", age: 30 };
      let str_obj = String(obj); // 객체를 문자열로 변환
      console.log(str_obj); // 출력: "[object Object]"
      ```

  + 배열을 문자열로 변환하기: 배열을 문자열로 변환할 때는 배열의 각 요소를 쉼표로 구분한 문자열로 변환합니다.
    + ```javascript
      let arr = [1, 2, 3];
      let str_arr = String(arr); // 배열을 문자열로 변환
      console.log(str_arr); // 출력: "1,2,3"
      ```

  `String()` 함수는 각 데이터 형식에 대해 적절한 문자열로 변환해줍니다. 이를 활용하여 다양한 상황에서 문자열로의 변환을 수행할 수 있습니다.

이렇게 `String()`에 대해 한번 알아보았습니다. 그럼 일단 코드를 만들고 코드를 설명해 드리겠습니다.

```javascript
function solution(n) {
  n = String(n);
  var answer = 0;
  for(let i = 0; i<n.length; i++){
    answer += Number(n[i]);
  }
  return answer;
}
```
위 코드가 오늘의 완성 코드입니다. 하나씩 한번 알아보겠습니다.


```javascript
n = String(n);
```
매개변수로 받아온 `n`을 `String()`을 이용해 문자열로 변경하였습니다. 


```javascript
for(let i = 0; i<n.length; i++){
  answer += Number(n[i]);
}
```
반복문을 이용해 문자열인 `n`의 `index`값으로 각 자릿수를 `Number()`내장함수로 다시 정수로 변환해 `answer`변수에 `+=`연산자를 이용하여 추가해주었습니다.

이렇게 반복문을 작성해 `n`의 각 자릿수의 합을 알아보았습니다.

```javascript
function solution(n) {
  n = String(n);
  var answer = 0;
  for(let i = 0; i<n.length; i++){
    answer += Number(n[i]);
  }
  return answer;
}
```

문제의 식이 완성되었으니 프로그래머스에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/자릿수더하기_02.jpg)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '자릿수 더하기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.