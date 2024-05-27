---
layout: post
title: 프로그래머스 LV1 "나누어 떨어지는 숫자 배열"
date: 2024-05-12 23:03 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv1 나누어 떨어지는 숫자 배열

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 문제 '나누어 떨어지는 숫자 배열' 문제입니다.

  왜 LV2를 이어서 안올리냐 라고 물어보신다면.. 솔직히 너무 레벨0,1을 20개만 하고 올라간 제가 오만했습니다. 조금 더 공부를 하며 기초 공부를 하면서 다시 올라가보겠습니다..
  오늘부터는 몇번째 문제 등등의 글은 넣지 않고 문제에 집중한 포스팅을 하겠습니다.

  우선 문제를 바로 풀러 가보겠습니다.

  ![프로그래머스 이미지](/assets/img//post45_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 배열 `arr`와 정수 `divisor`가 주어질 때, `arr`의 요소 중 `divisor`로 나누어 떨어지는 값들을 오름차순으로 정렬한 배열을 반환하는 것입니다. 만약 나누어 떨어지는 요소가 하나도 없다면 배열에 `-1`을 담아 반환합니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(arr, divisor) {
  var answer = [];
  return answer;
}
```

우선 함수 안에 매개변수로 `arr`와 `divisor`가 있습니다. 출제자가 해당 매개변수에 임의의 값을 넣어주면 함수의 리턴 값으로 답을 알려주면 되는 간단한 코드입니다.

그럼 코드의 결과를 한번 작성해 보겠습니다.

```javascript
function solution(arr, divisor) {
  var answer = [];
  arr.forEach(e=>{
    if(e%divisor == 0){
      answer.push(e)
    }
  })
  if(answer.length <= 0) {
    answer = [-1];
  }else {
    answer.sort((a, b) => a - b)
  }
  return answer;
}
```
위 코드의 간단한 설명을 알려드리겠습니다.

1. 함수 solution은 매개변수로 배열 arr와 정수 divisor를 받습니다.

2. answer 변수를 빈 배열로 초기화합니다.

3. arr 배열의 각 요소를 순회하며, 현재 요소 e가 divisor로 나누어 떨어지는지 확인합니다. 만약 나누어 떨어진다면 answer 배열에 e를 추가합니다.

4. 배열 arr를 모두 순회한 후, answer 배열의 길이가 0인지 확인합니다. 만약 길이가 0이라면 -1을 배열에 담아 반환합니다.

5. 길이가 0이 아니라면, answer 배열을 오름차순으로 정렬합니다.

6. 최종적으로 answer 배열을 반환합니다.

그럼 문제의 식이 완성되었으니 프로그래머스에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img//post45_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) Lv1 '나누어 떨어지는 숫자 배열' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.