---
layout: post
title: 프로그래머스 LV0 "양꼬치"
date: 2024-05-23 14:50 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv0]
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV0 양꼬치

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV0 문제 '양꼬치' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post51_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 `n`과 `k`가 주어집니다. 각 매개변수를 조건에 맞는 계산을 한 후 모두 더한뒤 출력하는 간단한 산수 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(n, k) {
  var answer = 0;
  return answer;
}
```

기본 세팅 코드는 매개변수 `n`과 `k`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이전 포스팅에서 다룬적이 있던 삼항 연산자를 이용해 문제를 해결해보도록 하겠습니다.

## 삼항 연산자

삼항 연산자는 조건부 연산자로, 조건에 따라 다른 값을 반환하도록 도와줍니다. 기본적인 구문은 다음과 같습니다:

```javascript
  condition ? exprIfTrue : exprIfFalse
```

여기서 `condition`은 평가할 조건을 나타내며, `exprIfTrue`는 조건이 참일 때 반환할 값이고, `exprIfFalse`는 조건이 거짓일 때 반환할 값입니다.

예를 들어, 다음은 삼항 연산자를 사용하여 간단한 예제를 표현한 것입니다:

```javascript
var age = 20;
var status = (age >= 18) ? '성인' : '미성년자';
console.log(status); // 출력 결과: '성인'
```

위 예제에서는 `age`가 18 이상인 경우에는 '성인'을 반환하고, 그렇지 않은 경우에는 '미성년자'를 반환합니다.

삼항 연산자는 조건문을 짧고 간결하게 작성할 수 있도록 도와줍니다. 하지만 과용되면 코드의 가독성을 해칠 수 있으므로 적절하게 사용해야 합니다.

그럼 삼항 연산자로 `num`의 나머지 수가 0이면 짝수이니 나누기 2를, 0이 아니면 3을 곱한뒤 1을 더해주는 식을 써보겠습니다.

```javascript
num = num%2 == 0? num / 2 : num * 3 + 1;
```

그럼 이 삼항 연산자를 이용해 문제를 완성해 보겠습니다.

```javascript
function solution(n, k) {
  var answer = 0;
  answer = (n*12000)+(k*2000)-(n >= 10 ? Math.floor(n/10) *2000 :0 );
  return answer;
}
```

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post51_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '양꼬치' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.