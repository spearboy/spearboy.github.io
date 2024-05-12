---
layout: post
title: 프로그래머스 LV1 "가운데 글자 가져오기"
date: 2024-04-29 15:51 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv1 가운데 글자 가져오기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 열두번째 문제 '가운데 글자 가져오기' 문제입니다.

  ![프로그래머스 이미지](https://spearboy.github.io/assets/img/가운데글자가져오기_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 `s`라는 문자열이 주어지면 해당 문자열안에 가운데에 해당하는 요소를 찾아 출력하는 문제입니다.

  오늘 문제에서는 간단한 조건문으로 문제를 해결해 보겠습니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(s) {
  var answer = '';
  return answer;
}
```

기본 세팅 코드는 간단하게 `s`라는 문자열 형태의 매개변수를 전달하며 함수 내에 `answer`변수를 선언해 리턴하는 기본적인 함수의 형태입니다.

문제의 핵심은 문자열이 짝수라면 가운데에 해당하는 2글자를 출력하고, 문자열이 홀수라면 가운데에 해당하는 1글자만 출력하는것입니다.

여기서 알 수 있는것은 우선 문자열이 짝수인지 홀수인지 구분을 해야하는것입니다.

홀수와 짝수를 구분하는 방법은 이전 포스팅에서 많이 다뤘었던 나머지 연산자로 처리를 하면 될것입니다.

우선 나머지 연산자로 홀수와 짝수를 구하는 방법을 코드로 작성해보겠습니다.

```javascript
function solution(s) {
  var answer = '';
  if(s.length%2 == 0){
    answer = "짝수";
  }else {
    answer = "홀수";
  }
  return answer;
}
```

위 코드처럼 조건문으로 `s`의 `length`값에서 2를 나누고 나머지수가 0 이라면 짝수일것이고, 0이 아니라면 홀수일것입니다.

이렇게 짝수와 홀수를 판별하는 식이 완성 되었습니다. 그럼 문자열의 가운데 값을 가져오기만 하면 됩니다.

문자열은 `index`값을 알 수 있으니 해당 문자열의 가운데 `index`값이 몇인지만 알면 쉽게 해결이 가능할것입니다. 

우선 홀수부터 코드를 작성해보겠습니다.

```javascript
function solution(s) {
  var answer = '';
  if(s.length%2 == 0){
    answer = "짝수";
  }else {
    answer = s[Math.trunc(s.length/2)];
  }
  return answer;
}
```

위 코드에서 홀수 부분에 넣은 코드를 설명 드리겠습니다. 우선 `s`의 `index`값을 가져오기 위해 `[]`안에 `Math.trunc((s.length/2))`를 넣어주어
반으로 나눈값의 소수점을 버려 정수로 만들어 가운데 글자를 가져왔습니다.
예를들어 문자열이 "abcde"라면 각각 카운트하는 방법이 `index`는 0,1,2,3,4 이고 `length`는 1,2,3,4,5입니다. 그럼 `length`에서 2를 나누면 5나누기 2는 2.5 이고 소수점을 버린다면 2가 될것입니다.
이 값을 `index`위치에 대치해보면 0,1,2,3,4임으로 가운데 값인 2를 가져올것입니다.

이렇게 홀수를 완성했으니 짝수를 한번 다시 해보겠습니다.

```javascript
function solution(s) {
  var answer = '';
  if(s.length%2 == 0){
    answer = s[(s.length/2)-1] + s[s.length/2];
  }else {
    answer = s[Math.trunc(s.length/2)];
  }
  return answer;
}
```

짝수의 경우에는 중간에 위치한 두 문자를 가져와야 하므로, 문자열의 길이를 2로 나눈 값에서 1을 빼고, 그 값과 나눈 값을 인덱스로 사용하여 해당 두 문자를 가져오는 것으로 설명했습니다.

이렇게 문제의 식이 완성 되었습니다. 완성된 코드를 다시 한번 보여드리겠습니다.

```javascript
function solution(s) {
  var answer = '';
  if(s.length%2 == 0){
    answer = s[(s.length/2)-1] + s[s.length/2];
  }else {
    answer = s[Math.trunc(s.length/2)];
  }
  return answer;
}
```

문제의 식이 완성되었으니 프로그래머스에 한번 확인해보겠습니다.

![프로그래머스 이미지](https://spearboy.github.io/assets/img/가운데글자가져오기_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '가운데 글자 가져오기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.