---
layout: post
title: 프로그래머스 LV2 "짝지어 제거하기"
date: 2024-06-03 23:02 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 짝지어 제거하기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '짝지어 제거하기' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 문자열 `S`에서 같은 알파벳이 2개 붙어 있는 짝을 찾아 제거하고, 이 과정을 반복해서 문자열을 모두 제거할 수 있는지를 확인하는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(s) {
    var answer = 0;
    return answer;
}
```

기본 세팅 코드는 매개변수 `s`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `스택` 자료구조를 사용하여 풀어보겠습니다.

## 스택을 사용한 풀이

스택은 후입선출(LIFO) 구조로, 가장 나중에 들어간 데이터가 가장 먼저 나오는 특성을 가집니다. 이 특성을 이용하면 짝지어 제거하기 문제를 효율적으로 해결할 수 있습니다.

### 문제 해결 방법

1. 문자열을 순차적으로 탐색하면서 각 문자를 스택에 넣습니다.
2. 스택의 최상단 문자와 현재 문자가 같으면 스택에서 최상단 문자를 제거합니다.
3. 문자열을 끝까지 탐색한 후 스택이 비어있으면 모든 문자를 제거할 수 있다는 의미로 1을 반환하고, 그렇지 않으면 0을 반환합니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(s) {
    let stack = [];
    for (let i = 0; i < s.length; i++) {
        if (stack.length > 0 && stack[stack.length - 1] === s[i]) {
            stack.pop();
        } else {
            stack.push(s[i]);
        }
    }
    return stack.length === 0 ? 1 : 0;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `let stack = [];`: 빈 스택을 선언합니다.
2. `for (let i = 0; i < s.length; i++) {`: 문자열 `s`를 처음부터 끝까지 탐색합니다.
3. `if (stack.length > 0 && stack[stack.length - 1] === s[i]) {`: 스택이 비어있지 않고, 최상단 문자와 현재 문자가 같으면,
   - `stack.pop();`: 스택의 최상단 문자를 제거합니다.
4. `else { stack.push(s[i]); }`: 그렇지 않으면 현재 문자를 스택에 넣습니다.
5. `return stack.length === 0 ? 1 : 0;`: 스택이 비어있으면 1을, 그렇지 않으면 0을 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.


![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '짝지어 제거하기' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.