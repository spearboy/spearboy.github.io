---
layout: post
title: 프로그래머스 LV2 "괄호 회전하기"
date: 2024-06-07 05:07 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV2 괄호 회전하기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 문제 '괄호 회전하기' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 문자열 `s`를 왼쪽으로 회전시켜 올바른 괄호 문자열이 되게 하는 경우의 수를 찾는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(s) {
    var answer = -1;
    return answer;
}
```

기본 세팅 코드는 매개변수 `s`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `스택` 자료구조를 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. 문자열 `s`를 왼쪽으로 회전시키면서 각 회전된 문자열이 올바른 괄호 문자열인지 확인합니다.
2. 올바른 괄호 문자열인지 확인하기 위해 `스택`을 사용합니다.
3. 문자열을 순회하면서 여는 괄호는 스택에 넣고, 닫는 괄호는 스택의 최상단 값과 매칭되는지 확인합니다.
4. 모든 회전된 문자열에 대해 올바른 괄호 문자열인지 확인하여 그 개수를 셉니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(s) {
    function isValid(s) {
        const stack = [];
        const pairs = { ')': '(', ']': '[', '}': '{' };
        for (const char of s) {
            if (char === '(' || char === '[' || char === '{') {
                stack.push(char);
            } else if (char === ')' || char === ']' || char === '}') {
                if (stack.pop() !== pairs[char]) {
                    return false;
                }
            }
        }
        return stack.length === 0;
    }
    
    let count = 0;
    for (let i = 0; i < s.length; i++) {
        if (isValid(s)) {
            count++;
        }
        s = s.slice(1) + s[0];
    }
    return count;
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `function isValid(s) {...}`: 주어진 문자열 `s`가 올바른 괄호 문자열인지 확인하는 함수입니다.
2. `const stack = [];`: 여는 괄호를 저장할 스택을 선언합니다.
3. `const pairs = { ')': '(', ']': '[', '}': '{' };`: 닫는 괄호에 대응하는 여는 괄호를 매핑한 객체입니다.
4. 문자열을 순회하면서 여는 괄호는 스택에 넣고, 닫는 괄호는 스택의 최상단 값과 매칭되는지 확인합니다.
5. 모든 괄호가 매칭되면 스택이 비어 있어야 올바른 괄호 문자열입니다.
6. `for (let i = 0; i < s.length; i++) {...}`: 문자열 `s`를 왼쪽으로 회전시키면서 각 회전된 문자열이 올바른 괄호 문자열인지 확인합니다.
7. `s = s.slice(1) + s[0];`: 문자열 `s`를 왼쪽으로 한 칸 회전시킵니다.
8. 올바른 괄호 문자열인 경우의 수를 세고 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '괄호 회전하기' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
