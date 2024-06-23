---
layout: post
title: 프로그래머스 LV2 "점프와 순간 이동"
date: 2024-06-04 13:13 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 점프와 순간 이동

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '점프와 순간 이동' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 거리 `N`을 `K` 칸 점프 또는 순간 이동으로 최소한의 건전지 사용량으로 이동하는 방법을 찾는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(n) {
    var answer = 0;
    return answer;
}
```

기본 세팅 코드는 매개변수 `n`이 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `이진법`과 관련이 있습니다.

## 문제 해결 방법

1. `N`이 짝수이면 순간 이동이 가능합니다. (`N // 2`)
2. `N`이 홀수이면 1칸 점프하여 건전지 사용량이 증가합니다. (`N - 1`)

이 과정을 `N`이 0이 될 때까지 반복하면 됩니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(n) {
    let battery = 0;
    while (n > 0) {
        if (n % 2 === 0) {
            n = Math.floor(n / 2);
        } else {
            n -= 1;
            battery += 1;
        }
    }
    return battery;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `let battery = 0;`: 건전지 사용량을 저장할 변수를 선언합니다.
2. `while (n > 0) {`: `N`이 0보다 클 때까지 반복합니다.
3. `if (n % 2 === 0) { n = Math.floor(n / 2); }`: `N`이 짝수이면 순간 이동을 하고, `N`을 절반으로 줄입니다.
4. `else { n -= 1; battery += 1; }`: `N`이 홀수이면 1칸 점프하고, 건전지 사용량을 1 증가시킵니다.
5. `return battery;`: 총 건전지 사용량을 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.


![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머머스](https://programmers.co.kr/) LV2 '점프와 순간 이동' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
