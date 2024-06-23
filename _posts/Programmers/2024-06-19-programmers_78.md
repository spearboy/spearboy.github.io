---
layout: post
title: 프로그래머스 LV1 "폰켓몬"
date: 2024-06-19 08:25 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV1 폰켓몬

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 문제 '폰켓몬' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 배열 `nums`에서 N/2 마리의 폰켓몬을 선택할 때 최대한 많은 종류의 폰켓몬을 선택하는 것입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(nums) {
    var answer = 0;
    return answer;
}
```

기본 세팅 코드는 매개변수 `nums`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `해시셋`을 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. 배열 `nums`에서 중복을 제거하여 폰켓몬 종류의 개수를 셉니다.
2. `N/2`와 폰켓몬 종류의 개수를 비교하여 더 작은 값을 반환합니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(nums) {
    const uniquePokemon = new Set(nums);
    return Math.min(uniquePokemon.size, nums.length / 2);
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `const uniquePokemon = new Set(nums);`: 배열 `nums`에서 중복을 제거하여 폰켓몬 종류의 개수를 셉니다.
2. `return Math.min(uniquePokemon.size, nums.length / 2);`: `N/2`와 폰켓몬 종류의 개수를 비교하여 더 작은 값을 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '폰켓몬' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
