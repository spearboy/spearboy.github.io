---
layout: post
title: 프로그래머스 LV0 "나이 출력"
date: 2024-04-03 17:59 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv0]
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv0 나이 출력

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 여섯번째 문제 '나이 출력' 문제입니다.

  ![프로그래머스 이미지](/assets/img/나이출력_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 'age'값이 주어지면 해당 값이 몇년생인지 출력해야하는 문제 입니다.
  
  이번에문제에서는 산술 연산자를 사용해보겠습니다.

  이제 기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(age) {
    var answer = 0;
    return answer;
}
``` 
이전 포스팅과 같은 기본 함수형태이지만 값은 'age' 1개뿐입니다.

우선 함수안에 매개변수로 num1,num2가 있습니다. 출제자가 해당 매개변수에 임의의 값을 넣어주면
함수의 리턴 값으로 답을 알려주면 되는 간단한 코드 입니다.

나이를 구해야하니 저희는 한번 계산을 해봐야겠죠?
간단한 산술 문제입니다. 'age'가 만약 10이라고 가정하고 현재는 2022년입니다. 현재 문제의 기준은 2022년 입니다.
그럼 계산식은 쉽게 2022 - 'age' 즉, 2020 - 10이 되는거죠.

그럼 바로 시작해볼까요?

```javascript
function solution(age) {
    var answer = (2022 - age);
    return answer;
}
console.log(solution(10))
``` 

위 코드의 결과는 2012입니다.

저는 이 함수의 매개변수에 10을 넣어줬습니다. 
그리고 아래 결과값을 확인하기 위해 console.log()으로 콘솔에 값을 볼 수 있게 했습니다.

이제 프로그래머스에서 결과를 확인해 보겠습니다.

![프로그래머스 이미지](/assets/img/나이출력_02.png)

결과는 전부 불일치가 나왔습니다.   
예상 답들이 전부 1씩 낮게 나왔네요. 원하는 답이 어떤식으로 나오는지 알았으니 코드를 수정해보겠습니다.


```javascript
function solution(age) {
    var answer = 2022 - (age-1);
    return answer;
}
console.log(solution(10))
``` 
매개변수에서 받아오는 값을 -1 해주었습니다.
그럼 다시한번 제출해보도록 하겠습니다.

![프로그래머스 이미지](/assets/img/나이출력_03.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '나이 출력' 문제의 대해서 알아봤습니다.

감사합니다.