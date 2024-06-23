---
layout: post
title: 프로그래머스 LV1 "이상한 문자 만들기"
date: 2024-06-17 10:57 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV1 이상한 문자 만들기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 문제 '이상한 문자 만들기' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post56_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 주어진 문자열 `s`에서 각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 반환하는 것입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(s) {
    var answer = '';
    return answer;
}
```

기본 세팅 코드는 매개변수 `s`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

이번 문제는 `문자열 처리`를 사용하여 해결할 수 있습니다.

## 문제 해결 방법

1. 문자열을 단어별로 분리합니다.
2. 각 단어의 짝수번째 문자를 대문자로, 홀수번째 문자를 소문자로 변환합니다.
3. 변환된 단어들을 다시 합쳐서 결과 문자열을 만듭니다.

그럼 코드를 작성해 보겠습니다.

```javascript
function solution(s) {
    return s.split(' ').map(word => {
        return word.split('').map((char, index) => {
            return index % 2 === 0 ? char.toUpperCase() : char.toLowerCase();
        }).join('');
    }).join(' ');
}
```

위 코드의 간단한 설명을 알려드리겠습니다.

1. `s.split(' ')`: 문자열을 공백을 기준으로 분리하여 단어 배열을 만듭니다.
2. `word.split('').map((char, index) => { ... }).join('')`: 각 단어를 문자 배열로 분리하여 짝수 인덱스는 대문자로, 홀수 인덱스는 소문자로 변환한 후 다시 합칩니다.
3. `s.split(' ').map(word => { ... }).join(' ')`: 변환된 단어 배열을 다시 공백을 기준으로 합쳐서 최종 문자열을 만듭니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/post56_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '이상한 문자 만들기' 문제에 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런 방법도 있구나 하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.
