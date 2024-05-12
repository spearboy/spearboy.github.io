---
layout: post
title: 프로그래머스 LV0 "두 수의 차"
date: 2024-03-29 09:44 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv0]
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv0 두 수의 차

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  우선 첫번째 시작은 '두 수의 차' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post01_01.jpg)

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

### 여기서 매개변수란?

자바스크립트의 매개변수는 함수가 호출될 때 함수에 전달되는 값입니다.
함수 내부에서 이 값을 지정하여 사용할 수 있습니다.
매개변수는 함수의 정의 부분에서 지정되며, 함수가 호출될 때 전달된 값이 매개변수에 할당됩니다.

이제 이 함수가 어떻게 작동하는지 한번 이 함수를 호출해서 확인해보겠습니다.

```javascript
function solution(num1, num2) {
    var answer = 0;
    return answer;
}
console.log(solution(1, 2))
``` 

저는 이 함수의 매개면수에 1과2를 넣어줬습니다. 
그리고 아래 결과값을 확인하기 위해 console.log()으로 콘솔에 값을 볼 수 있게 했습니다.
한번 결과값을 보겠습니다.

결과는 0 이 나왔습니다.

함수 내부에 answer 이라는 변수가 있고 그변수를 리턴하는 함수 입니다.
이제 코드를 이렇게 바꿔 보겠습니다.

```javascript
function solution(num1, num2) {
    var answer = num1;
    return answer;
}
console.log(solution(1, 2))
``` 

이제 결과값이 1이 되었습니다. 이유는 answer 이라는 변수에 매개변수 num1 을 할당하여
answer 이라는 변수를 즉 num1 으로 변경한것입니다.
(쉽게 말하면 그냥 개명한겁니다ㅋ)

이제 매개변수를 변수로 변환하는 방법을 알았습니다.

그럼 다시 문제를 보시면 num1 에서 num2을 뺀 값을 return 하라고 하네요.
결국 num1 - num2 라는 말이죠

이제 코드를 넣어보겠습니다.

```javascript
function solution(num1, num2) {
    var answer = num1-num2;
    return answer;
}
console.log(solution(1, 2))
``` 

결과는 -1 입니다.
성공적으로 문제를 풀었습니다.

이제 이 코드를 [프로그래머스](https://programmers.co.kr/)에서 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post01_02.jpg)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '두 수의 차' 문제의 대해서 알아봤습니다.

감사합니다.
