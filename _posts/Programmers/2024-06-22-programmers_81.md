---
layout: post
title: 프로그래머스 LV2 "타겟 넘버"
date: 2024-06-22 06:36 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 타겟 넘버

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '타겟 넘버' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 배열 `numbers`와 `target`을 사용하여 타겟 넘버를 만드는 방법의 수를 찾는 것입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(numbers, target) {
    var answer = 0;
    return answer;
}
```

기본 세팅 코드는 매개변수 `numbers`와 `target`이 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `DFS` 또는 `BFS`를 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. DFS를 사용하여 모든 가능한 경우의 수를 탐색합니다.
2. 타겟 넘버와 일치하는 경우의 수를 카운트합니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(numbers, target) {
    let answer = 0;
    
    function dfs(index, sum) {
        if (index === numbers.length) {
            if (sum === target) {
                answer++;
            }
            return;
        }
        dfs(index + 1, sum + numbers[index]);
        dfs(index + 1, sum - numbers[index]);
    }
    
    dfs(0, 0);
    
    return answer;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `let answer = 0;`: 타겟 넘버와 일치하는 경우의 수를 카운트할 변수를 선언합니다.
2. `function dfs(index, sum) { ... }`: DFS를 사용하여 모든 가능한 경우의 수를 탐색하는 함수입니다.
3. `if (index === numbers.length) { if (sum === target) { answer++; } return; }`: 모든 숫자를 탐색한 경우 타겟 넘버와 일치하면 카운트합니다.
4. `dfs(index + 1, sum + numbers[index]);`: 현재 숫자를 더하는 경우를 탐색합니다.
5. `dfs(index + 1, sum - numbers[index]);`: 현재 숫자를 빼는 경우를 탐색합니다.
6. `dfs(0, 0);`: 초기 호출로 인덱스 0과 합계 0을 사용하여 DFS를 시작합니다.
7. `return answer;`: 타겟 넘버를 만드는 방법의 수를 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '타겟 넘버' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
