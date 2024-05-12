---
layout: post
title: 프로그래머스 LV0 "각도기"
date: 2024-04-09 09:59 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv0]
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv0 각도기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 열두번째 문제 '각도기' 문제입니다.

  ![프로그래머스 이미지](/assets/img/각도기_01.jpg)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수 `angle`이 주어지면   
  `angle`이 0 초과 90 미만은 1   
  `angle`이 90이면 2   
  `angle`이 90 초과 180 미만은 3   
  `angle`이 180이면 4   
  위 조건에 맞춰 출력하는 문제입니다.

  이번문제에서는 이전에 사용했던 조건문(비교문)을 사용해보도록 하겠습니다.

  이제 기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(angle) {
  var answer = 0;
  return answer;
}
``` 
기존과 같은 기본 함수의 형태입니다. 이번엔 함수에서 `angle`이라는 매개변수를 입력하고 있습니다.   
이번문제에서는 앞서 말씀드렸던 조건문을 사용하여 문제를 풀어보겠습니다.   
조건문(비교문)에 대해서는 이전 포스팅인 [숫자 비교하기](https://spearboy.github.io/posts/programmers_5/#비교문if문) 포스팅에서 확인하실 수 있습니다.   

우선 모든 첫번째 조건인 0초과 90 미만이니 0~89 까지의 숫자를 1이라고 지정을 해야합니다.
여기서 저는 `&&` 연산자를 사용해 2가지 조건이 만족하면 1을 지정하도록 하겠습니다.
```javascript
function solution(angle) {
    var answer = 0;
    if(0 < angle && 90 > angle){
        answer = 1;
    }
    return answer;
}
``` 

이제 첫번째 조건이 완성 되었으니 이후 추가 조건을 만들어 90은 2를 지정하도록 하겠습니다.
```javascript
function solution(angle) {
    var answer = 0;
    if(0 < angle && 90 > angle){
        answer = 1;
    } else if( angle == 90) {
        answer = 2;
    }
    return answer;
}
``` 

이제 세번째 조건은 첫번째 조건과 90 초과 180 미만이니 91~179까지의 숫자를 3이라고 지정하도록 하겠습니다.
```javascript
function solution(angle) {
    var answer = 0;
    if(0 < angle && 90 > angle){
        answer = 1;
    } else if( angle == 90) {
        answer = 2;
    } else if(90 < angle && 180 > angle){
        answer = 3;
    }
    return answer;
}
``` 
마지막으로 네번째 조건은 두번째 조건과 마찬가지로 180일때 4를 지정하도록 하겠습니다.
```javascript
function solution(angle) {
  var answer = 0;
  if(0 < angle && 90 > angle){
    answer = 1;
  } else if( angle == 90) {
    answer = 2;
  } else if(90 < angle && 180 > angle){
    answer = 3;
  } else {
    answer = 4;
  }
  return answer;
}
``` 
코드가 완성 되었으니 프로그래머스에서 결과를 확인해 보겠습니다.

```javascript
function solution(n) {
  var answer = 0;
  if(0 < angle && 90 > angle){
    answer = 1;
  } else if( angle == 90) {
    answer = 2;
  } else if(90 < angle && 180 > angle){
    answer = 3;
  } else {
    answer = 4;
  }
  return answer;
}
``` 
제출용으로 정리한 코드는 위와 같습니다.

![프로그래머스 이미지](/assets/img/각도기_02.jpg)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '각도기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.