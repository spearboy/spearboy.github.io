---
layout: post
title: 프로그래머스 LV1 "두 정수 사이의 합"
date: 2024-04-27 20:11 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv1 두 정수 사이의 합

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 열번째 문제 '두 정수 사이의 합' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post30_01.jpg)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 정수 `a`와 `b`가 주어지면 `a`와 `b`를 포함한 사이의 정수들의 합을 출력하는 문제입니다.

  오늘 문제에서는 간단한 반복문과 조건문으로 문제를 해결해 보겠습니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(a, b) {
  var answer = 0;
  return answer;
}
```

기본 세팅 코드는 간단하게 `a`와 `b`라는 매개변수를 전달하며 함수 내에 `answer`변수를 선언해 리턴하는 기본적인 함수의 형태입니다.

이 기본 함수에 이번 문제의 핵심인 두 정수 사이의 합을 출력하는것이 목표입니다. 예를 들어 매개변수에 1과 10을 넣어 주었다면 1+2+3+4+5+6+7+8+9+10인 55를 리턴하는것입니다.

여기서 우선 알 수 있는 방법은 매개변수간의 수만큼 반복해야 한다는 것입니다.

하지만 매개변수 `a`와 `b`중 누가 더 큰 수인지 확인을 해야합니다.

그럼 코드로 작성하고 다시 설명 드리겠습니다.

```javascript
function solution(a, b) {
  var answer = 0;
  let i,j;
  if(a >= b){
    i = b;
    j = a;
  }else {
    i = a;
    j = b;
  }
  return answer;
}
```
위 코드와 같이 작성을 해주었습니다. `let i,j`는 `i`라는 변수와 `j`라는 변수를 선언해주었고, 조건문에서는 `a`가 `b`보다 크거나 같다면 `i`에 `b`를 담고 `j`에 `a`를 담습니다. 그게 아니라면 `i`에 `a`를 담고 `j`에 `b`를 담아 주었습니다.

이렇게 해서 반복문에 사용할 변수가 완성 된것입니다.

우선 이번에 사용할 반복문인 `while()`에 대해 설명을 하고 문제를 다시 풀어보겠습니다.
물론 이전 포스팅에서 한번 설명 드렸지만 이번 포스팅에서 다시한번 설명을 드리겠습니다.

## while()

`while` 루프는 조건이 참인 동안에 코드 블록을 계속해서 실행합니다. 조건이 거짓이 되면 루프가 종료됩니다. 이 때문에 `while` 루프는 조건이 참인 동안 반복 실행됩니다.

`while` 루프의 구조는 다음과 같습니다.

```javascript
while (condition) {
  // 조건이 참일 때 실행되는 코드
}
```

여기서 `condition`은 `boolean`값 (`true`(참) 또는 `false`(거짓))을 반환하는 표현식입니다. `condition`이 참일 때에만 코드 블록이 실행됩니다. 따라서 `condition`이 거짓이 되면 루프가 종료됩니다.

예를 들어, `while` 루프를 사용하여 숫자 1부터 5까지 출력하는 코드를 작성할 수 있습니다.

```javascript
let i = 1;
while (i <= 5) {
  console.log(i);
  i++;
}
```

이 코드는 i가 5보다 작거나 같은 동안에는 i의 값을 출력하고 i를 1씩 증가시킵니다. 결과적으로 1부터 5까지의 숫자가 출력됩니다.


이렇게 `while()`에 대해 알아 보았습니다. 그럼 `while()`을 이용해 식을 완성해 보도록 하겠습니다.

```javascript
function solution(a, b) {
  var answer = 0;
  let i,j;
  if(a >= b){
    i = b;
    j = a;
  }else {
    i = a;
    j = b;
  }
  while(i <= j){
    answer += i;
    i++;
  }
  return answer;
}
```

문제의 식이 완성되었으니 프로그래머스에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post30_02.jpg)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '두 정수 사이의 합' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.