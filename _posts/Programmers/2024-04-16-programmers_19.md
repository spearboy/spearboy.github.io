---
layout: post
title: 프로그래머스 LV0 "피자 나눠 먹기 (1)"
date: 2024-04-16 22:17 +0900
description: 
image: ../../assets/img/programmers_logo.png
category: [programmers, Lv0]
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv0 피자 나눠 먹기 (1)

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 열아홉번째 문제 '피자 나눠 먹기 (1)' 문제입니다.

  ![프로그래머스 이미지](../../assets/img/피자나눠먹기_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수 `n`이 주어지면 7으로 나눈 숫자를 반올림해 출력하는 문제입니다. 이번문제는 조금 처음에 했던 문제들처럼 단순한 계산 문제입니다.

  그럼 문제를 한번 풀어보겠습니다.

  이번문제에서는 정수를 반환해주는 `Math.ceil()`을 사용해서 문제를 풀어보도록 하겠습니다. 
  정수를 반환하는 함수들은 이전 포스팅인 [프로그래머스 Lv0 몫 구하기](https://spearboy.github.io/posts/programmers_2/)에서 확인 가능합니다.

  이제 기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(n) {
  var answer = 0;
  return answer;
}
``` 
기존과 같은 기본 함수의 형태입니다. 이번엔 함수에서 `n`라는 매개변수를 입력하고 있습니다.
이번 문제에서는 정말 간단한 수식인 `/`을 사용해 문제를 풀어보겠습니다.

여기서 사용하는 이유는 다른 정수를 반환해주는 함수인 `Math.floor()`,`Math.round()`,`Math.trunc()`는 정수로 올리거나 내리지만 이번문제와는 적합하지 않습니다.

왜냐하면 이번문제에 입출력예시에서는 15를 입력했을때 3이 출력되야하는것을 보실수 있습니다.
그렇기 때문에 소수점이 나오는 순간 무조건 반올림을 해야 해당 입출력의 조건을 만족하게 될겁니다.

또 반올림을 해주는 `Math.round()`를 사용하지 않는 이유는 위 이유와 같이 무조건 반올림이 아니라 소수점 이하 값이 0.5 이상이면 올림하고, 0.5 미만이면 내리기 때문입니다.

예시를 보여드리겠습니다.

우선 모든 테스트의 매개변수는 15으로 정하고 결과는 3이 나와야합니다.

첫번째 `Math.floor()`입니다.
```javascript
function solution(n) {
  var answer = 0;
  answer = Math.floor(n/7);
  return answer;
}
console.log(solution(15))
```
결과는 2 입니다. 테스트결과가 3이 아니라 실패입니다.

두번째 `Math.round()`입니다.
```javascript
function solution(n) {
  var answer = 0;
  answer = Math.round(n/7);
  return answer;
}
console.log(solution(15))
```
결과는 2 입니다. 마찬가지로 테스트결과가 3이 아니라 실패입니다.

세번째 `Math.trunc()`입니다.
```javascript
function solution(n) {
  var answer = 0;
  answer = Math.trunc(n/7);
  return answer;
}
console.log(solution(15))
```
결과는 2 입니다. 마찬가지로 테스트결과가 3이 아니라 실패입니다.

네번째 `Math.ceil()`입니다.
```javascript
function solution(n) {
  var answer = 0;
  answer = Math.ceil(n/7);
  return answer;
}
console.log(solution(15))
```
결과는 3 입니다. 원하는 결과인 3이 나왔습니다.
설명한것과 같이 코드들의 다른점을 확인해보았습니다.

그럼 이제 4번의 코드로 프로그래머스에서 결과를 확인해 보겠습니다.

![프로그래머스 이미지](../../assets/img/피자나눠먹기_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '피자 나눠 먹기 (1)' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.