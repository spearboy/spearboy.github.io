---
layout: post
title: 프로그래머스 LV0 "두 수의 나눗셈"
date: 2024-04-07 22:30 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv0]
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv0 두 수의 나눗셈

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 열번째 문제 '두 수의 나눗셈' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post10_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수 `num1`과`num2`가 주어지면 `num1`에서 `num2`를 나눈값에 1000을 곱해 출력하는 문제입니다.

  이번문제에서는 이전에 사용했던 정수 반환 메서드를 사용해보겠습니다.

  이제 기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(num1, num2) {
  var answer = 0;
  return answer;
}
``` 
기존과 같은 기본 함수의 형태입니다. 이번엔 함수에서 `num1`과`num2` 이라는 문자열을 매개변수로 입력하고 있습니다.

정수를 반환 하려면 저희는 이전 포스팅에서 사용했던 [정수 반환 메서드](https://spearboy.github.io/posts/programmers_2/)를 사용해보겠습니다.


처음 시도해볼 메서드는 `Math.floor()`입니다.
```javascript
function solution(num1, num2) {
  var answer = Math.floor((num1/num2)*1000);
  return answer;
}
``` 
프로그래머스 출력값은 아래와 같습니다.
  + 테스트 1
    + 입력값 〉	3, 2
    + 기댓값 〉	1500
    + 실행 결과 〉	테스트를 통과하였습니다.
  + 테스트 2
    + 입력값 〉	7, 3
    + 기댓값 〉	2333
    + 실행 결과 〉	테스트를 통과하였습니다.
  + 테스트 3
    + 입력값 〉	1, 16
    + 기댓값 〉	62
    + 실행 결과 〉	테스트를 통과하였습니다.   
`Math.floor()`메서드는 주어진 숫자를 그보다 작거나 같은 가장 큰 정수로 내림합니다. 이번 문제의 테스트에 적합한 메서드 입니다.   

두번째로 시도해볼 메서드는 `Math.ceil()`입니다.   
```javascript
function solution(num1, num2) {
  var answer = Math.ceil((num1/num2)*1000);
  return answer;
}
``` 
프로그래머스 출력값은 아래와 같습니다.   
  + 테스트 1
    + 입력값 〉	3, 2
    + 기댓값 〉	1500
    + 실행 결과 〉	테스트를 통과하였습니다.
  + 테스트 2
    + 입력값 〉	7, 3
    + 기댓값 〉	2333
    + 실행 결과 〉	실행한 결괏값 2334이 기댓값 2333과 다릅니다.
  + 테스트 3
    + 입력값 〉	1, 16
    + 기댓값 〉	62
    + 실행 결과 〉	실행한 결괏값 63이 기댓값 62과 다릅니다.   
`Math.ceil()`메서드는 주어진 숫자를 그보다 크거나 같은 가장 작은 정수로 올립니다. 출력 결과에서 보시는 바와 같이 정수의 값을 변경됨으로 이문제에서 사용할 수 없습니다.   

세번째로 시도해볼 메서드는 `Math.round()`입니다.   
```javascript
function solution(num1, num2) {
  var answer = Math.round((num1/num2)*1000);
  return answer;
}
``` 
프로그래머스 출력값은 아래와 같습니다.   
  + 테스트 1
    + 입력값 〉	3, 2
    + 기댓값 〉	1500
    + 실행 결과 〉	테스트를 통과하였습니다.
  + 테스트 2
    + 입력값 〉	7, 3
    + 기댓값 〉	2333
    + 실행 결과 〉	테스트를 통과하였습니다.
  + 테스트 3
    + 입력값 〉	1, 16
    + 기댓값 〉	62
    + 실행 결과 〉	실행한 결괏값 63이 기댓값 62과 다릅니다.   
`Math.round()`메서드는 주어진 숫자를 가장 가까운 정수로 반올림합니다. 출력 결과에서 보시는 바와 같이 정수의 값을 변경됨으로 이문제에서 사용할 수 없습니다. 

마지막 네번째로 시도해볼 메서드는 `Math.trunc()`입니다.   
```javascript
function solution(num1, num2) {
  var answer = Math.trunc((num1/num2)*1000);
  return answer;
}
``` 
프로그래머스 출력값은 아래와 같습니다.   
  + 테스트 1
    + 입력값 〉	3, 2
    + 기댓값 〉	1500
    + 실행 결과 〉	테스트를 통과하였습니다.
  + 테스트 2
    + 입력값 〉	7, 3
    + 기댓값 〉	2333
    + 실행 결과 〉	테스트를 통과하였습니다.
  + 테스트 3
    + 입력값 〉	1, 16
    + 기댓값 〉	62
    + 실행 결과 〉	테스트를 통과하였습니다.   
`Math.trunc()`메서드는 주어진 숫자의 소수 부분을 버립니다. `Math.floor()`메서드와 같이 정수의 값이 변경되지 않아 이번 문제의 테스트에 적합한 메서드 입니다.    

이제 원하는 결과를 출력할 수 있는 2가지 메서드중 저는 마지막 메서드인 `Math.trunc()`을 사용해 프로그래머스에서 결과를 확인해 보겠습니다.

```javascript
function solution(num1, num2) {
  var answer = Math.trunc((num1/num2)*1000);
  return answer;
}
``` 
제출용으로 정리한 코드는 위와 같습니다.

![프로그래머스 이미지](/assets/img/post10_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '두 수의 나눗셈' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.