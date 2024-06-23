---
layout: post
title: 프로그래머스 LV2 "튜플"
date: 2024-06-13 07:57 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 튜플

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '튜플' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 문자열 `s`가 표현하는 튜플을 배열에 담아 반환하는 것입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(s) {
    var answer = [];
    return answer;
}
```

기본 세팅 코드는 매개변수 `s`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `파싱`과 `정렬`을 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. 문자열 `s`를 파싱하여 각 집합을 추출합니다.
2. 집합을 원소의 개수에 따라 정렬합니다.
3. 각 집합을 순회하며 원소를 추가합니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(s) {
    const sets = s.slice(2, -2).split("},{").map(set => set.split(",").map(Number));
    sets.sort((a, b) => a.length - b.length);
    
    const result = new Set();
    sets.forEach(set => set.forEach(num => result.add(num)));
    
    return Array.from(result);
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `const sets = s.slice(2, -2).split("},{").map(set => set.split(",").map(Number));`: 문자열 `s`를 파싱하여 각 집합을 추출합니다.
2. `sets.sort((a, b) => a.length - b.length);`: 집합을 원소의 개수에 따라 정렬합니다.
3. `const result = new Set();`: 결과를 저장할 `Set` 객체를 생성합니다.
4. `sets.forEach(set => set.forEach(num => result.add(num)));`: 각 집합을 순회하며 원소를 추가합니다.
5. `return Array.from(result);`: `Set` 객체를 배열로 변환하여 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '튜플' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
