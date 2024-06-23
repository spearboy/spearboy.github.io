---
layout: post
title: 프로그래머스 LV2 "전화번호 목록"
date: 2024-06-12 00:46 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 전화번호 목록

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '전화번호 목록' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 배열 `phone_book`에서 어떤 번호가 다른 번호의 접두어인 경우가 있는지 확인하는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(phone_book) {
    var answer = true;
    return answer;
}
```

기본 세팅 코드는 매개변수 `phone_book`이 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `정렬`과 `해시맵`을 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. 전화번호 배열을 정렬합니다.
2. 정렬된 배열을 순회하며 현재 번호가 다음 번호의 접두어인지 확인합니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(phone_book) {
    phone_book.sort();
    
    for (let i = 0; i < phone_book.length - 1; i++) {
        if (phone_book[i + 1].startsWith(phone_book[i])) {
            return false;
        }
    }
    
    return true;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `phone_book.sort();`: 전화번호 배열을 정렬합니다.
2. `for (let i = 0; i < phone_book.length - 1; i++) { ... }`: 정렬된 배열을 순회합니다.
3. `if (phone_book[i + 1].startsWith(phone_book[i])) { return false; }`: 현재 번호가 다음 번호의 접두어인지 확인합니다. 접두어인 경우 `false`를 반환합니다.
4. `return true;`: 모든 번호가 다른 번호의 접두어가 아닌 경우 `true`를 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '전화번호 목록' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
