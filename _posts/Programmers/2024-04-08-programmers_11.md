---
layout: post
title: 프로그래머스 LV0 "짝수의 합"
date: 2024-04-08 21:21 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv0]
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv0 짝수의 합

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 열한번째 문제 '짝수의 합' 문제입니다.

  ![프로그래머스 이미지](/assets/img/짝수의합_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수 `n`이 주어지면 `n`이하의 모든 짝수를 합한 값을 출력하는 문제입니다.

  이번문제에서는 이전에 사용했던 반복문을 사용해보도록 하겠습니다.

  이제 기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(n) {
  var answer = 0;
  return answer;
}
``` 
기존과 같은 기본 함수의 형태입니다. 이번엔 함수에서 `n`이라는 매개변수를 입력하고 있습니다.   
이번문제에서는 앞서 말씀드렸던 반복문을 사용하여 문제를 풀어보겠습니다.   
반복문에 대해서는 이전 포스팅인 [배열의 평균값](https://spearboy.github.io/posts/programmers_8/#%EB%B0%98%EB%B3%B5%EB%AC%B8%EC%9D%B4%EB%9E%80) 포스팅에서 확인하실 수 있습니다.   

우선 모든 짝수를 찾으려면 이전에 사용했었던 나머지 연산자 `%`를 사용해서 짝수를 구하고 우선 테스트를 위해 배열에 담아서 확인해보도록 하겠습니다.   
```javascript
function solution(n) {
  var answer = 0;
  let g = [];
  for(let i = 0; i<n; i++){
    if(i%2 == 0){
        g.push(i);
    }
  }
  return g;
}
console.log(solution(10))
``` 
위 코드의 출력 결과는 `[0,2,4,6,8]`입니다. 하지만 여기서 10의 짝수중 10이 나오지 않았습니다.
이유는 반복문의 조건에 있습니다. 반복문의 조건이 `i < n`이면 10이아닌 9에서 반복문의 조건이 `false`를 반환하며 반복문이 종료됩니다.
여기서 해결 방법은 2가지가 있습니다. 조건의 `i < n`을 `i <= n`으로 변경하는것과 `i < n+1`으로 변경하는것 입니다.   

첫번째로 `i <= n`으로 변경하게 되면 `n`의 수 까지 조건을만족하여 10을 반환할 수 있습니다.   

두번째로 `i < n+1`으로 변경하게 되면 `n`의 수가 11이 됨으로, 10을 반환할 수 있습니다. 

저는 첫번째 방법으로 시도해보겠습니다.   

```javascript
function solution(n) {
  var answer = 0;
  let g = [];
  for(let i = 0; i<=n; i++){
    if(i%2 == 0){
        g.push(i);
    }
  }
  return g;
}
console.log(solution(10))
``` 
위 코드의 출력 결과는 `[0,2,4,6,8,10]`입니다. 이제 저희는 모든 짝수의 값을 구할 수 있게 되었습니다.
그럼 이제 바로 `answer`변수에 `+=`연산자로 추가해보겠습니다.

```javascript
function solution(n) {
  var answer = 0;
  for(let i = 0; i<=n; i++){
    if(i%2 == 0){
        answer+=i;
    }
  }
  return answer;
}
console.log(solution(10))
``` 
위 코드의 출력 결과는 `30`입니다. 성공적으로 짝수의 합을 구했으니 프로그래머스에서 결과를 확인해 보겠습니다.

```javascript
function solution(n) {
  var answer = 0;
  for(let i = 0; i<=n; i++){
    if(i%2 == 0){
        answer+=i;
    }
  }
  return answer;
}
``` 
제출용으로 정리한 코드는 위와 같습니다.

![프로그래머스 이미지](/assets/img/짝수의합_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '짝수의 합' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.