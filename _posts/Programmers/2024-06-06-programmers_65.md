---
layout: post
title: 프로그래머스 LV2 "예상 대진표"
date: 2024-06-06 00:11 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 예상 대진표

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '예상 대진표' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 게임 참가자 수 `N`, 참가자 번호 `A`와 `B`가 몇 번째 라운드에서 만나는지를 찾는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(n, a, b) {
    var answer = 0;

    // [실행] 버튼을 누르면 출력 값을 볼 수 있습니다.
    console.log('Hello Javascript')

    return answer;
}
```

기본 세팅 코드는 매개변수 `n`, `a`, `b`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `토너먼트 방식`을 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. 참가자 번호 `A`와 `B`를 1씩 감소시켜 0 기반 인덱스로 변환합니다.
2. `A`와 `B`가 같아질 때까지 반복합니다.
3. 각 라운드마다 `A`와 `B`를 각각 2로 나눈 몫으로 업데이트하고 라운드 수를 증가시킵니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(n, a, b) {
    let round = 0;
    a -= 1;
    b -= 1;
    
    while (a !== b) {
        a = Math.floor(a / 2);
        b = Math.floor(b / 2);
        round += 1;
    }
    
    return round;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `let round = 0;`: 라운드 수를 저장할 변수를 선언합니다.
2. `a -= 1; b -= 1;`: `A`와 `B`를 0 기반 인덱스로 변환합니다.
3. `while (a !== b) {`: `A`와 `B`가 같아질 때까지 반복합니다.
4. `a = Math.floor(a / 2); b = Math.floor(b / 2);`: 각 라운드마다 `A`와 `B`를 각각 2로 나눈 몫으로 업데이트합니다.
5. `round += 1;`: 라운드 수를 증가시킵니다.
6. `return round;`: `A`와 `B`가 처음 만나는 라운드 수를 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '예상 대진표' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
