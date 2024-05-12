---
layout: post
title: 프로그래머스 LV0 "짝수 홀수 개수"
date: 2024-04-12 19:54 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv0]
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv0 짝수 홀수 개수

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 열다섯번째 문제 '짝수 홀수 개수' 문제입니다.

  ![프로그래머스 이미지](https://spearboy.github.io/assets/img/짝수홀수개수_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수 `num_list`이 배열로 주어지면 `num_list`안에 짝수와 홀수가 각각 몇개인지 출력하는 문제입니다.

  이번문제에서도 이전 포스팅과 같이 반복문과 조건문(비교문)을 사용해보도록 하겠습니다.

  이제 기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(num_list) {
  var answer = [];
  return answer;
}
``` 
기존과 같은 기본 함수의 형태입니다. 이번엔 함수에서 `num_list`이라는 매개변수를 입력하고 있습니다.
반복문은 이전 포스팅인 [배열의 평균값](https://spearboy.github.io/posts/programmers_8/#반복문이란) 포스팅에서 확인하실 수 있고,   
조건문(비교문)에 대해서는 이전 포스팅인 [숫자 비교하기](https://spearboy.github.io/posts/programmers_5/#비교문if문) 포스팅에서 확인하실 수 있습니다.   

조건은 배열로 들어오는 `num_list`의 몇번째 요소가 짝수인지 홀수인지 체크를 하면서 배열의 형태로 반환해야합니다.

이번엔 조건을 먼저 작성해보도록 하겠습니다. 조건식을 작성하는데 저희는 짝수와 홀수를 구분을 하는 조건식이 필요합니다. 이때 사용할 수 있는 연산자가 하나 있습니다. 이전 포스팅에 연산자에 대해 한번 다뤄봤었습니다. 바로 나머지 연산자인 `%`입니다. 나머지 연산자는 주어진 숫자를 다른 숫자로 나눈 후 남는 나머지를 반환합니다. 예를 들어, `5 % 2`는 1을 반환하며, 5를 2로 나눈 후 남는 나머지인 1을 나타냅니다. 이 연산자는 주로 숫자의 홀수/짝수 여부를 판별하거나 순환적인 작업에서 활용됩니다.

그럼 한번 조건식을 한번 작성해보겠습니다. 
```javascript
function solution(num_list) {
  var answer = [0,0];
    if(num_list[0]%2 == 0){
      answer[0]++;
    }else {
      answer[1]++;
    }
  return answer;
}
``` 
저는 다른 서드를 사용하지 않고 그냥 미리 `answer` 안에 0을 입력해주고
조건식으로 `num_list`의 0번째 `index`자리에 수를 나머지 연산자로 2를 나눠서 0이 나온다면 짝수임으로 `answer`의 0번째 `index`자리에 `++`으로 1을 증가시켜주는 조건식을 만들었습니다.

그럼 이제 반복문을한번 만들어보겠습니다. 이번 포스팅에서는 일반적은`for`반복문을 사용하겠습니다.
```javascript
function solution(num_list) {
  var answer = [0,0];
  for(let i=0; i<num_list.length; i++){
    if(num_list[i]%2 == 0){
      answer[0]++;
    }else {
      answer[1]++;
    }
  }
  return answer;
}
``` 
이렇게 반복문을 만들어보았습니다. 반복문의 내용은 `num_list`의 길이만큼만 반복하는 루프입니다. 코드가 완성되었으니 한번 제출해보겠습니다.

![프로그래머스 이미지](https://spearboy.github.io/assets/img/짝수홀수개수_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '짝수 홀수 개수' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.