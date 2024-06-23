---
layout: post
title: 프로그래머스 LV2 "할인 행사"
date: 2024-06-08 03:22 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 할인 행사

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '할인 행사' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 문자열 배열 `want`, 정수 배열 `number`, 문자열 배열 `discount`를 사용하여 회원등록시 원하는 제품을 모두 할인 받을 수 있는 날짜의 총 일수를 찾는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(want, number, discount) {
    var answer = 0;
    return answer;
}
```

기본 세팅 코드는 매개변수 `want`, `number`, `discount`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `슬라이딩 윈도우`와 `해시맵`을 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. `want`와 `number`를 사용하여 필요한 제품의 해시맵을 만듭니다.
2. `discount` 배열에서 첫 10일간의 제품 수량을 해시맵으로 만듭니다.
3. 해시맵을 비교하여 필요한 제품 수량과 일치하는지 확인합니다.
4. 슬라이딩 윈도우 기법을 사용하여 첫 10일 이후의 구간을 검사합니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(want, number, discount) {
    let answer = 0;
    
    const needed = {};
    for (let i = 0; i < want.length; i++) {
        needed[want[i]] = number[i];
    }
    
    for (let i = 0; i <= discount.length - 10; i++) {
        const current = {};
        for (let j = 0; j < 10; j++) {
            if (current[discount[i + j]] === undefined) {
                current[discount[i + j]] = 0;
            }
            current[discount[i + j]] += 1;
        }
        
        let valid = true;
        for (let item of Object.keys(needed)) {
            if (current[item] !== needed[item]) {
                valid = false;
                break;
            }
        }
        
        if (valid) {
            answer += 1;
        }
    }
    
    return answer;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `let answer = 0;`: 가능한 날짜의 총 일수를 저장할 변수를 선언합니다.
2. `const needed = {};`: 필요한 제품의 해시맵을 만듭니다.
3. `for (let i = 0; i < want.length; i++) { ... }`: `want`와 `number`를 사용하여 해시맵을 채웁니다.
4. `for (let i = 0; i <= discount.length - 10; i++) { ... }`: 첫 10일 이후의 구간을 검사합니다.
5. `const current = {};`: 현재 10일간의 제품 수량을 해시맵으로 만듭니다.
6. `for (let j = 0; j < 10; j++) { ... }`: 현재 10일간의 제품 수량을 해시맵으로 채웁니다.
7. `let valid = true;`: 필요한 제품 수량과 일치하는지 확인합니다.
8. `for (let item of Object.keys(needed)) { ... }`: 해시맵을 비교하여 필요한 제품 수량과 일치하는지 확인합니다.
9. `if (valid) { answer += 1; }`: 일치하면 가능한 날짜의 총 일수를 증가시킵니다.
10. `return answer;`: 가능한 날짜의 총 일수를 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '할인 행사' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
