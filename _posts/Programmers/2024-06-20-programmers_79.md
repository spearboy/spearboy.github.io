---
layout: post
title: 프로그래머스 LV1 "달리기 경주"
date: 2024-06-20 12:07 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV1 달리기 경주

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 문제 '달리기 경주' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 배열 `players`와 `callings`를 사용하여 경주가 끝났을 때 선수들의 이름을 1등부터 순서대로 반환하는 것입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(players, callings) {
    var answer = [];
    return answer;
}
```

기본 세팅 코드는 매개변수 `players`와 `callings`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `배열 처리`를 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. `callings` 배열을 순회하며 추월한 선수의 위치를 찾습니다.
2. 추월한 선수를 앞의 선수와 위치를 바꿉니다.
3. 최종 선수 배열을 반환합니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(players, callings) {
    for (const call of callings) {
        const index = players.indexOf(call);
        if (index > 0) {
            [players[index - 1], players[index]] = [players[index], players[index - 1]];
        }
    }
    return players;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `for (const call of callings) { ... }`: `callings` 배열을 순회합니다.
2. `const index = players.indexOf(call);`: 추월한 선수의 위치를 찾습니다.
3. `if (index > 0) { [players[index - 1], players[index]] = [players[index], players[index - 1]]; }`: 추월한 선수를 앞의 선수와 위치를 바꿉니다.
4. `return players;`: 최종 선수 배열을 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '달리기 경주' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
