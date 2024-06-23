---
layout: post
title: 프로그래머스 LV2 "피로도"
date: 2024-06-23 04:30 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 피로도

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '피로도' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 배열 `dungeons`와 현재 피로도 `k`를 사용하여 탐험할 수 있는 최대 던전 수를 찾는 것입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(k, dungeons) {
    var answer = -1;
    return answer;
}
```

기본 세팅 코드는 매개변수 `k`와 `dungeons`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `백트래킹`을 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. 모든 가능한 던전 탐험 순서를 시도합니다.
2. 각 순서에 대해 탐험할 수 있는 최대 던전 수를 계산합니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(k, dungeons) {
    let maxDungeons = 0;
    
    function explore(currentK, count, visited) {
        maxDungeons = Math.max(maxDungeons, count);
        
        for (let i = 0; i < dungeons.length; i++) {
            if (!visited[i] && currentK >= dungeons[i][0]) {
                visited[i] = true;
                explore(currentK - dungeons[i][1], count + 1, visited);
                visited[i] = false;
            }
        }
    }
    
    explore(k, 0, Array(dungeons.length).fill(false));
    
    return maxDungeons;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `let maxDungeons = 0;`: 탐험할 수 있는 최대 던전 수를 저장할 변수를 선언합니다.
2. `function explore(currentK, count, visited) { ... }`: 백트래킹을 사용하여 모든 가능한 던전 탐험 순서를 시도하는 함수입니다.
3. `maxDungeons = Math.max(maxDungeons, count);`: 현재 탐험한 던전 수를 최대값으로 업데이트합니다.
4. `for (let i = 0; i < dungeons.length; i++) { if (!visited[i] && currentK >= dungeons[i][0]) { ... } }`: 방문하지 않은 던전 중 현재 피로도가 최소 필요 피로도 이상인 던전을 탐험합니다.
5. `visited[i] = true; explore(currentK - dungeons[i][1], count + 1, visited); visited[i] = false;`: 현재 던전을 방문하고 탐험한 후 다시 미방문 상태로 되돌립니다.
6. `explore(k, 0, Array(dungeons.length).fill(false));`: 초기 호출로 현재 피로도 `k`와 탐험한 던전 수 0, 미방문 상태 배열을 사용하여 백트래킹을 시작합니다.
7. `return maxDungeons;`: 탐험할 수 있는 최대 던전 수를 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '피로도' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
