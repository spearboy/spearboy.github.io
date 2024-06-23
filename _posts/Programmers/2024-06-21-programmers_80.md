---
layout: post
title: 프로그래머스 LV2 "롤케이크 자르기"
date: 2024-06-21 22:12 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 롤케이크 자르기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '롤케이크 자르기' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 배열 `topping`에서 롤케이크를 공평하게 자르는 방법의 수를 찾는 것입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(topping) {
    var answer = -1;
    return answer;
}
```

기본 세팅 코드는 매개변수 `topping`이 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `슬라이딩 윈도우`를 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. 왼쪽과 오른쪽의 토핑 종류를 각각 집합으로 관리합니다.
2. 왼쪽 집합과 오른쪽 집합의 크기가 동일한 경우를 찾습니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(topping) {
    const leftSet = new Set();
    const rightSet = new Set(topping);
    const rightCount = new Array(topping.length).fill(0);
    let answer = 0;

    for (let i = 0; i < topping.length; i++) {
        rightCount[topping[i]] = (rightCount[topping[i]] || 0) + 1;
    }

    for (let i = 0; i < topping.length; i++) {
        leftSet.add(topping[i]);
        rightCount[topping[i]] -= 1;
        if (rightCount[topping[i]] === 0) {
            rightSet.delete(topping[i]);
        }
        if (leftSet.size === rightSet.size) {
            answer++;
        }
    }

    return answer;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `const leftSet = new Set(); const rightSet = new Set(topping);`: 왼쪽과 오른쪽의 토핑 종류를 각각 집합으로 관리합니다.
2. `const rightCount = new Array(topping.length).fill(0);`: 오른쪽 토핑의 개수를 카운트할 배열을 선언합니다.
3. `for (let i = 0; i < topping.length; i++) { rightCount[topping[i]] = (rightCount[topping[i]] || 0) + 1; }`: 오른쪽 토핑의 개수를 카운트합니다.
4. `for (let i = 0; i < topping.length; i++) { ... }`: 왼쪽과 오른쪽 토핑의 집합을 업데이트합니다.
5. `leftSet.add(topping[i]);`: 현재 토핑을 왼쪽 집합에 추가합니다.
6. `rightCount[topping[i]] -= 1;`: 현재 토핑의 오른쪽 개수를 감소시킵니다.
7. `if (rightCount[topping[i]] === 0) { rightSet.delete(topping[i]); }`: 현재 토핑의 오른쪽 개수가 0이 되면 오른쪽 집합에서 제거합니다.
8. `if (leftSet.size === rightSet.size) { answer++; }`: 왼쪽 집합과 오른쪽 집합의 크기가 동일한 경우를 찾습니다.
9. `return answer;`: 공평하게 자를 수 있는 방법의 수를 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '롤케이크 자르기' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
