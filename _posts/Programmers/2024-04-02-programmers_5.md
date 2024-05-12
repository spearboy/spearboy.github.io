---
layout: post
title: 프로그래머스 LV0 "숫자 비교하기"
date: 2024-04-02 16:48 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv0]
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv0 숫자 비교하기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 다섯번째 문제 '숫자 비교하기' 문제입니다.

  ![프로그래머스 이미지](https://spearboy.github.io/assets/img/숫자비교하기_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 1번 값과 2번값이 주어졌을때 1번값과 2번값이 같으면 1을, 다르면 2를 출력해야하는 문제입니다.   
  
  이번에문제에서는 비교문을 사용해보겠습니다.

  이제 기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(num1, num2) {
    var answer = 0;
    return answer;
}
``` 
이전 포스팅과 같은 기본 함수형태입니다.

우선 함수안에 매개변수로 num1,num2가 있습니다. 출제자가 해당 매개변수에 임의의 값을 넣어주면
함수의 리턴 값으로 답을 알려주면 되는 간단한 코드 입니다.

javascript비교문은 if 입니다.

### 비교문(if문)
  비교문은 javascript의 특정 값이나 숫자 또는 문자열 등을 비교할 수 있습니다. 비교문에는 연산자를 사용하게됩니다.
  예시:
  + if( A > B ) :  A는 B 보다 크다
  + if( A < B ) :  A는 B 보다 작다
  + if( A <= B) :  A는 B보다 작거나 같다
  + if( A >= B) :  A는 B보다 크거나 같다
  + if( A != B) :  A는 B와 같지 않다
  + if( A !== B) :  A는 B와 일치하지 않다
  + if( A == B) :  A는 B와 동등하다
  + if( A === B) :  A는 B와 일치한다
  
  이외 [연산자](https://spearboy.github.io/posts/programmers_3#연산자)는 이전 포스팅에서 확인 가능합니다.

비교문을 이용하여 한번 코드를 만들어보겠습니다.
```javascript
function solution(num1, num2) {
    var answer = 0;
    if(num1 == num2){
      answer = 1;
    }else {
      answer = 2;
    }
    return answer;
}
console.log(solution(1,1))
console.log(solution(1,2))
``` 

이번에도 2가지의 결과를 보도록 하겠습니다.

저는 이 함수의 매개변수에 1과1, 1과2 넣어줬습니다. 
그리고 아래 결과값을 확인하기 위해 console.log()으로 콘솔에 값을 볼 수 있게 했습니다.

비교문에대해 설명을 간단하게 하면 num1 과 num2가 같으면 answer에 1을 담아주고
else는 조건문이 거짓이라면 즉, 조건과 맞지 않으면 answer에 2를 담아줬습니다.

콘솔의 결과는 1과 2가 나왔습니다.

결과는 원하는대로 나왔으니 한번 제출해보도록 하겠습니다.

![프로그래머스 이미지](https://spearboy.github.io/assets/img/숫자비교하기_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '숫자 비교하기' 문제의 대해서 알아봤습니다.

감사합니다.