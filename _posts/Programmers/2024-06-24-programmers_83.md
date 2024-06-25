---
layout: post
title: 프로그래머스 LV2 "택배상자"
date: 2024-06-24 15:47 +0900
description:
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 택배상자

기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

오늘은 LV2 문제 '택배상자' 문제입니다.

![프로그래머스 이미지](/assets/img/post56_01.png)

위 이미지가 프로그래머스 코딩문제입니다.

문제는 주어진 배열 `order`를 사용하여 트럭에 실을 수 있는 최대 상자 수를 찾는 것입니다.

그럼 오늘의 문제를 한번 풀어보겠습니다.

기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(order) {
  var answer = 0;
  return answer;
}
```

기본 세팅 코드는 매개변수 `order`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `스택`을 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. 기본 컨테이너 벨트와 보조 컨테이너 벨트를 사용하여 상자를 실어야 합니다.
2. 스택을 사용하여 상자를 임시로 보관합니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(order) {
  const stack = [];
  let index = 0;
  for (let i = 1; i <= order.length; i++) {
    stack.push(i);
    while (stack.length && stack[stack.length - 1] === order[index]) {
      stack.pop();
      index++;
    }
  }
  return index;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `const stack = [];`: 임시로 상자를 보관할 스택을 선언합니다.
2. `let index = 0;`: 현재 처리할 상자의 인덱스를 초기화합니다.
3. `for (let i = 1; i <= order.length; i++) { ... }`: 1번부터 n번 상자까지 순서대로 처리합니다.
4. `stack.push(i);`: 현재 상자를 스택에 보관합니다.
5. `while (stack.length && stack[stack.length - 1] === order[index]) { stack.pop(); index++; }`: 스택의 상자가 현재 처리할 순서와 일치하면 스택에서 꺼내어 트럭에 실습니다.
6. `return index;`: 트럭에 실은 상자의 개수를 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '택배상자' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
