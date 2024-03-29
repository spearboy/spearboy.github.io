---
layout: post
title: 프로그래머스 LV0 
date: 2024-03-29 09:44 +0900
description: 
image: ../assets/img/programmers_logo.png
category: code
tags: code, lv0, programmers, javascript
published: true
sitemap: true
---

# 프로그래머스 Lv0 두 수의 차

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  우선 첫번째 시작은 '두 수의 차' 문제입니다.

  ![프로그래머스 이미지](../assets/img/두수의차_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 1번 값과 2번값이 주어졌을때 1번값 - 2번값의 값을 구하는 문제입니다.
  (그냥 뺄샘 문제입니다.)

  이제 기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(num1, num2) {
    var answer = 0;
    return answer;
}
``` 
우선 함수안에 매개변수로 num1,num2가 있습니다. 출제자가 해당 매개변수에 임의의 값을 넣어주면
함수의 리턴 값으로 답을 알려주면 되는 간단한 코드 입니다.