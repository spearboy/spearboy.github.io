---
layout: post
title: 프로그래머스 LV2 "구명보트"
date: 2024-06-05 21:13 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 구명보트

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '구명보트' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 사람들의 몸무게 배열 `people`과 구명보트의 무게 제한 `limit`이 주어졌을 때, 최소한의 구명보트 개수로 모든 사람을 구출하는 방법을 찾는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(people, limit) {
    var answer = 0;
    return answer;
}
```

기본 세팅 코드는 매개변수 `people`과 `limit`이 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `투 포인터` 방식을 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. `people` 배열을 정렬합니다.
2. 가장 가벼운 사람과 가장 무거운 사람을 한 조로 만들어 보트를 태웁니다.
3. 두 사람의 무게 합이 `limit`을 넘지 않으면 두 사람을 함께 태우고, 그렇지 않으면 무거운 사람만 태웁니다.
4. 이 과정을 반복하여 모든 사람을 구출합니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(people, limit) {
    people.sort((a, b) => a - b);
    let i = 0, j = people.length - 1;
    let boats = 0;
    
    while (i <= j) {
        if (people[i] + people[j] <= limit) {
            i++;
        }
        j--;
        boats++;
    }
    
    return boats;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `people.sort((a, b) => a - b);`: 사람들의 몸무게를 오름차순으로 정렬합니다.
2. `let i = 0, j = people.length - 1;`: `i`는 가장 가벼운 사람을, `j`는 가장 무거운 사람을 가리킵니다.
3. `while (i <= j) {`: `i`가 `j`보다 작거나 같은 동안 반복합니다.
4. `if (people[i] + people[j] <= limit) { i++; }`: 두 사람의 무게 합이 `limit`을 넘지 않으면 `i`를 증가시켜 다음 가벼운 사람을 가리킵니다.
5. `j--;`: 무거운 사람을 태웠으므로 `j`를 감소시킵니다.
6. `boats++;`: 보트 개수를 증가시킵니다.
7. `return boats;`: 총 필요한 보트 개수를 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.


![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머머스](https://programmers.co.kr/) LV2 '구명보트' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
