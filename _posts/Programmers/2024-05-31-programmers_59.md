---
layout: post
title: 프로그래머스 LV0 "암호 해독"
date: 2024-05-31 20:09 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv0]
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 LV0 암호 해독

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV0 문제 '암호 해독' 문제입니다.

  ![프로그래머스 이미지](/assets/img/post59_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 문자열 `cipher`와 정수 `code`가 주어지면 `cipher`의 `code`배수만큼 위치해있는 문자만 출력하는 문제입니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(cipher, code) {
  var answer = '';
  return answer;
}
```

기본 세팅 코드는 매개변수 `cipher`과 `code`가 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 리턴하는 간단한 기본 세팅 코드입니다.

문제의 요점은 만약 문자열로 `김김김머김김김슥김김김이`라는 문자열이 입력되고 4가 입력된다하면 문자열에 4의 배수에 해당하는 글자들만 골라 다시 문자를 만들어 출력하는 문제 입니다.

이런 문제에서는 반복문으로 해결 할 수 있을거같습니다.

그럼 오늘 문제의 풀이를 코드로 한번 작성해 보겠습니다.

```javascript
function solution(cipher, code) {
  var answer = '';
  for (var i = code - 1; i < cipher.length; i += code) {
    answer += cipher[i];
  }
  return answer
}
```
위 코드의 간단한 설명을 알려드리겠습니다.

1. 변수 초기화:
- `answer`라는 변수를 빈 문자열로 초기화합니다. 이 변수는 해독된 암호 문자열을 저장할 공간입니다.

2. 문자열 순회 및 문자 추출:
- `for` 루프를 사용하여 `cipher` 문자열을 순회합니다.
- 루프의 초기값 `i`는 `code - 1`입니다. 이는 0부터 시작하는 인덱스 기준으로 `code` 번째 위치를 맞추기 위해서입니다. 예를 들어, `code`가 3이면, 첫 번째 추출할 문자는 `cipher`의 2번째 인덱스에 위치한 문자입니다.
- 루프의 조건식 `i < cipher.length`는 인덱스 `i`가 `cipher` 문자열의 길이보다 작을 때까지 반복합니다.
- 루프의 증감식 `i += code`는 `i`의 값을 매번 `code`만큼 증가시킵니다. 즉, `i`는 `code`의 배수 위치를 가리키게 됩니다.
- 루프 내부에서 `cipher`의 인덱스 `i`에 해당하는 문자를 `answer` 문자열에 추가합니다.

3. 결과 반환:
- 루프가 끝난 후, 최종적으로 answer 문자열을 반환합니다.

그럼 코드를 [프로그래머스](https://programmers.co.kr/)에 한번 확인해보겠습니다.


![프로그래머스 이미지](/assets/img/post59_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '암호 해독' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.