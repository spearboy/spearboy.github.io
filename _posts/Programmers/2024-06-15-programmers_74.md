---
layout: post
title: 프로그래머스 LV2 "프로세스"
date: 2024-06-15 09:20 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 프로세스

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '프로세스' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 배열 `priorities`와 프로세스의 위치 `location`을 사용하여 해당 프로세스가 몇 번째로 실행되는지 찾는 것입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(priorities, location) {
    var answer = 0;
    return answer;
}
```

기본 세팅 코드는 매개변수 `priorities`와 `location`이 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `큐` 자료구조를 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. 큐를 사용하여 프로세스를 순서대로 처리합니다.
2. 큐에서 프로세스를 꺼내고, 우선순위가 높은 프로세스가 있는지 확인합니다.
3. 우선순위가 높은 프로세스가 있다면 다시 큐에 넣고, 없다면 실행합니다.
4. 실행된 프로세스가 목표 프로세스인지 확인합니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(priorities, location) {
    const queue = priorities.map((priority, index) => { return { priority, index }; });
    const result = [];
    
    while (queue.length) {
        const current = queue.shift();
        if (queue.some(process => process.priority > current.priority)) {
            queue.push(current);
        } else {
            result.push(current);
        }
    }
    
    return result.findIndex(process => process.index === location) + 1;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `const queue = priorities.map((priority, index) => { return { priority, index }; });`: 프로세스의 우선순위와 인덱스를 포함하는 큐를 생성합니다.
2. `const result = [];`: 실행된 프로세스를 저장할 배열을 선언합니다.
3. `while (queue.length) { ... }`: 큐가 빌 때까지 반복합니다.
4. `const current = queue.shift();`: 큐에서 현재 프로세스를 꺼냅니다.
5. `if (queue.some(process => process.priority > current.priority)) { queue.push(current); }`: 큐에 더 높은 우선순위의 프로세스가 있다면 현재 프로세스를 다시 큐에 넣습니다.
6. `else { result.push(current); }`: 그렇지 않다면 현재 프로세스를 실행하여 결과 배열에 추가합니다.
7. `return result.findIndex(process => process.index === location) + 1;`: 실행된 프로세스 중 목표 프로세스의 인덱스를 찾아 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '프로세스' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
