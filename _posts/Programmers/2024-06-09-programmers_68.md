---
layout: post
title: 프로그래머스 LV2 "기능개발"
date: 2024-06-09 13:58 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 기능개발

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '기능개발' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 배열 `progresses`와 `speeds`를 사용하여 각 배포마다 몇 개의 기능이 배포되는지를 찾는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(progresses, speeds) {
    var answer = [];
    return answer;
}
```

기본 세팅 코드는 매개변수 `progresses`와 `speeds`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `큐` 자료구조를 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. 각 기능이 완료되기까지 필요한 일수를 계산합니다.
2. 큐를 사용하여 기능의 완료 일수를 순차적으로 처리합니다.
3. 앞선 기능이 완료될 때까지 대기하는 기능들을 함께 배포합니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(progresses, speeds) {
    let answer = [];
    let days = progresses.map((progress, index) => Math.ceil((100 - progress) / speeds[index]));
    
    while (days.length > 0) {
        let currentDay = days.shift();
        let count = 1;
        
        while (days.length > 0 && days[0] <= currentDay) {
            days.shift();
            count++;
        }
        
        answer.push(count);
    }
    
    return answer;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `let answer = [];`: 각 배포마다 몇 개의 기능이 배포되는지를 저장할 배열을 선언합니다.
2. `let days = progresses.map((progress, index) => Math.ceil((100 - progress) / speeds[index]));`: 각 기능이 완료되기까지 필요한 일수를 계산하여 배열로 만듭니다.
3. `while (days.length > 0) { ... }`: 큐를 사용하여 기능의 완료 일수를 순차적으로 처리합니다.
4. `let currentDay = days.shift();`: 현재 기능의 완료 일수를 큐에서 꺼냅니다.
5. `let count = 1;`: 현재 기능과 함께 배포될 기능의 개수를 셉니다.
6. `while (days.length > 0 && days[0] <= currentDay) { ... }`: 앞선 기능이 완료될 때까지 대기하는 기능들을 함께 배포합니다.
7. `answer.push(count);`: 배포된 기능의 개수를 배열에 추가합니다.
8. `return answer;`: 각 배포마다 몇 개의 기능이 배포되는지를 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '기능개발' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
