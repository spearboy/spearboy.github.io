---
layout: post
title: 프로그래머스 LV1 "문자열을 정수로 바꾸기"
date: 2024-04-19 19:56 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv1 문자열을 정수로 바꾸기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 두번째 문제 '문자열을 정수로 바꾸기' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post22_01.jpg)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 문자열`s`가 주어지면 문자열인 `s`를 숫자로 변경해 출력하는 간단한 문제입니다.

  오늘은 문제에서 사용할 `Number()`내장함수 를 설명 드리겠습니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(s) {
  var answer = 0;
  return answer;
}
```
기본 세팅코드는 간단하게 `s`라는 매개변수를 전달하며 함수내에 `answer`변수를 선언해 리턴하는 기본적인 함수의 형태입니다.

오늘의 문제는 간단한 부분이니 사용될 내장함수인 `Number()`에 대해 설명드리겠습니다.

### Number()

  `Number()`는 JavaScript에서 사용되는 내장 함수 중 하나입니다. 이 함수는 주어진 값(value)을 숫자로 변환합니다.   
  주로 문자열을 숫자로 변환할 때 사용됩니다. 예를 들어 문제에서 보시는바와 같이 "1234"와 같은 문자열을 숫자 1234로 변환하고자 할 때 유용합니다.

  ```javascript
  let text = "1234";
  let number = Number(text);
  console.log(number); // 출력: 1234
  ```

  하지만 주의할 점이 있습니다. `Number()` 함수가 변환할 수 없는 문자열을 받을 경우 NaN (Not a Number)을 반환한다는 것입니다.

  ```javascript
  let text = "text";
  let number = Number(text);
  console.log(number); // 출력: NaN
  ```

  한가지 더, 다른 데이터 타입을 숫자로 변환할 수도 있습니다. 예를 들어 `boolean` 값을 숫자로 변환하면 `true`는 1, `false`는 0으로 변환됩니다.

  ```javascript
  let bool = true;
  let number = Number(bool);
  console.log(number); // 출력: 1

  bool = false;
  number = Number(bool);
  console.log(number); // 출력: 0
  ```

  산술 연산자중 `+`,`-` 기호가 앞에 붙어있을경우에는 양수 또는 음수로 변환도 가능합니다. 예를 들어 "+1234"는 양수인 1234으로, "-1234"는 음수인 -1234으로 변환됩니다.
   
  ```javascript
  let text = "+1234";
  let number = Number(text);
  console.log(number); // 출력: 1234

  text = "-1234";
  number = Number(text);
  console.log(number); // 출력: -1234
  ```

이렇게 `Number()`에 대해 알아보았습니다. `Number()`함수에 대해 추가로 궁금하신 부분은 콘솔에서 테스트해보시는것을 추천드립니다.   

그럼 문제 해결중 가장 중요한 `Number()`함수에 대해 알아보았으니 한번 코드로 작성해보겠습니다.

```javascript
function solution(s) {
  var answer = 0;
  answer = Number(s);
  return answer;
}
```

이렇게 코드를 작성해보았습니다. 저는 `answer`변수에 `s`매개변수를 `Number()`함수를 이용해 정수로 변환해 할당해주었습니다.
이렇게 완성된 코드를 프로그래머스에서 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post22_02.jpg)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '문자열을 정수로 바꾸기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.