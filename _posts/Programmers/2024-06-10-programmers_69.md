---
layout: post
title: 프로그래머스 LV2 "귤 고르기"
date: 2024-06-10 07:24 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 귤 고르기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '귤 고르기' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 배열 `tangerine`에서 `k`개의 귤을 선택하여 최소한의 종류로 구성하는 방법을 찾는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(k, tangerine) {
    var answer = 0;
    return answer;
}
```

기본 세팅 코드는 매개변수 `k`와 `tangerine`이 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `정렬`과 `그리디` 알고리즘을 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. 귤의 크기별로 개수를 셉니다.
2. 개수가 많은 순서대로 귤을 선택합니다.
3. 선택한 귤의 종류 수를 반환합니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(k, tangerine) {
    const count = {};
    
    tangerine.forEach(t => {
        count[t] = (count[t] || 0) + 1;
    });
    
    const sortedCounts = Object.values(count).sort((a, b) => b - a);
    
    let total = 0;
    let types = 0;
    
    for (const c of sortedCounts) {
        total += c;
        types++;
        if (total >= k) break;
    }
    
    return types;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `const count = {};`: 귤의 크기별로 개수를 셀 객체를 선언합니다.
2. `tangerine.forEach(t => { ... });`: 각 귤의 크기를 순회하며 개수를 셉니다.
3. `const sortedCounts = Object.values(count).sort((a, b) => b - a);`: 개수가 많은 순서대로 정렬합니다.
4. `let total = 0; let types = 0;`: 선택한 귤의 총 개수와 종류 수를 저장할 변수를 선언합니다.
5. `for (const c of sortedCounts) { ... };`: 개수가 많은 순서대로 귤을 선택합니다.
6. `total += c; types++;`: 선택한 귤의 개수와 종류 수를 증가시킵니다.
7. `if (total >= k) break;`: 선택한 귤의 총 개수가 `k` 이상이면 종료합니다.
8. `return types;`: 선택한 귤의 종류 수를 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '귤 고르기' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
