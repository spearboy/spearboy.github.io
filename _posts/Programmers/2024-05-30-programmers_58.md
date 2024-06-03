---
layout: post
title: 프로그래머스 LV0 "가위 바위 보"
date: 2024-05-22 21:28 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv0]
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV0 가위 바위 보

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV0 문제 '가위 바위 보' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post58_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 `rsp`가 주어집니다. 해당 문자열의 해당하는 숫자를 `rsp`값의 순서대로 출력하는 간단한 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(rsp) {
  var answer = '';
  return answer;
}
```

기본 세팅 코드는 매개변수 `rsp`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

오늘 문제는 가위바위보 처럼 주어지는 `rsp`문자열에 해당하는 모든 수를 리턴해줘야하는 문제입니다.

해당 문제는 간단하게 반복문과 조건문으로 처리 할 수 있습니다.

우선 2는 0으로, 0은 5, 5는 2로 대치해서 출력하면 되느 문제입니다. 여기서 알 수 있는것은 3가지 조건이 나온다는 것입니다.

이렇게 3가지 조건을 가지며 `rsp`문자열의 길이 만큼 반복해주는 반복문을 작성하면 문제는 해결될것입니다.

그럼 오늘 문제의 풀이를 코드로 한번 작성해 보겠습니다.

```javascript
function solution(rsp) {
  var answer = '';
  for(var i=0; i<rsp.length; i++){
    if(rsp[i] == 2){
      answer += '0';
    }else if(rsp[i] == 0){
      answer += '5';
    }else if(rsp[i] == 5){
      answer += '2';
    }
  }
  return answer;
}
```
위 코드의 간단한 설명을 알려드리겠습니다.

1. 반복문을 설정해 `rsp`의 `length`만큼 반복을 시켜줍니다.

2. 반복문 안에 조건을 설정해 해당 수를 `answer`안에 추가해 넣어줍니다.

3. 최종적으로 `answer`에 담긴 문자열을 리턴해줍니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post58_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '가위 바위 보' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.