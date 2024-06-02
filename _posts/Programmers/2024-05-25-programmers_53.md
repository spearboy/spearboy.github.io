---
layout: post
title: 프로그래머스 LV0 "아이스 아메리카노"
date: 2024-05-25 21:28 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv0]
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 lv0 아이스 아메리카노

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 lv0 문제 '아이스 아메리카노' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post53_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 `money`가 주어집니다. 5500으로 나눈 수 와 나머지값을 출력하는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(money) {
  var answer = [];
  return answer;
}
```

기본 세팅 코드는 매개변수 `money`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

오늘 문제의 핵심을 간단하게 문제를 풀어보면

1. 받은 돈을 5500으로 나누어 최대한 많은 아메리카노를 사야 합니다.

2. 남은 돈을 계산하여 반환해야 합니다.

그럼 오늘 문제의 풀이를 코드로 한번 작성해 보겠습니다.

```javascript
function solution(money) {
  var answer = [];
  var pricePerAmericano = 5500;
  var maxAmericano = Math.floor(money / pricePerAmericano);
  var remainingMoney = money % pricePerAmericano;
  
  answer = [maxAmericano, remainingMoney];
  return answer;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `pricePerAmericano` 변수에는 아메리카노 한 잔의 가격인 `5500`을 저장합니다.

2. `maxAmericano` 변수에는 입력된 돈을 아메리카노 한 잔의 가격으로 나눈 몫을 저장합니다. 이는 최대로 살 수 있는 아메리카노의 잔 수를 의미합니다.

3. `remainingMoney` 변수에는 입력된 돈을 아메리카노 한 잔의 가격으로 나눈 나머지를 저장합니다. 이는 아메리카노를 사고 남은 돈을 의미합니다.

4. `answer` 배열에 `maxAmericano`과 `remainingMoney`를 순서대로 담고, 이를 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post53_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '아이스 아메리카노' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.