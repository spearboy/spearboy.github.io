---
layout: post
title: 프로그래머스 LV0 "몫 구하기"
date: 2024-03-30 20:21 +0900
description: 
image: ../assets/img/programmers_logo.png
category: code
tags: code, lv0, programmers, javascript
published: true
sitemap: true
---

# 프로그래머스 Lv0 몫 구하기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 두번째 문제 '몫 구하기' 문제입니다.

  ![프로그래머스 이미지](../assets/img/몫구하기_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 1번 값과 2번값이 주어졌을때 1번값을 2번값으로 나눴을때의 값을 구하는 문제입니다.
  (그냥 나누기 문제입니다.)

  이제 기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(num1, num2) {
    var answer = 0;
    return answer;
}
``` 
이전 포스팅과 같은 기본 함수형태입니다.

우선 함수안에 매개변수로 num1,num2가 있습니다. 출제자가 해당 매개변수에 임의의 값을 넣어주면
함수의 리턴 값으로 답을 알려주면 되는 간단한 코드 입니다.

[매개변수](https://spearboy.github.io/posts/first-blog-post/#%EC%97%AC%EA%B8%B0%EC%84%9C-%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98%EB%9E%80)의 설명은 이전 포스팅을 참고해주세요.

바로 나누기를 해보겠습니다. javascript의 나누기 기호는 "/" 입니다.

```javascript
function solution(num1, num2) {
    var answer = num1/num2;
    return answer;
}
console.log(solution(10, 5))
``` 

저는 이 함수의 매개변수에 10과5를 넣어줬습니다. 
그리고 아래 결과값을 확인하기 위해 console.log()으로 콘솔에 값을 볼 수 있게 했습니다.
한번 결과값을 보겠습니다.

결과는 2가 나왔습니다.

나누기가 끝났으니 한번 제출해보도록 하겠습니다.

![프로그래머스 이미지](../assets/img/몫구하기_02.png)

?.... 오답이 나왔습니다. 문제가 뭔지 한번 알아보겠습니다.

이제보니 예시 출력 결과에서 홀수인 7 을 2로 나눴을때 3으로, 즉 정수를 반환해야 통과되는 문제였습니다.

이제 다시 코드를 수정하겠습니다.

여기서 정수를 반환해주는 javascript의 함수가 있습니다.
Math.floor(), Math.ceil(), Math.round() 그리고 Math.trunc()가 있습니다.
각 함수에 대한 설명과 예시를 알려드리겠습니다.

### Math.floor()
주어진 숫자를 그보다 작거나 같은 가장 큰 정수로 내림합니다. 즉, 소수점 이하를 버립니다. 음수인 경우에는 더욱 작아지므로 더욱 음의 방향으로 가까운 정수로 내림됩니다.
+ 예시 :
    + Math.floor(5.95)는 5를 반환합니다.
    + Math.floor(-5.95)는 -6을 반환합니다.

### Math.ceil()
주어진 숫자를 그보다 크거나 같은 가장 작은 정수로 올립니다. 즉, 소수점 이하를 올립니다. 음수인 경우에는 더욱 커지므로 더욱 양의 방향으로 가까운 정수로 올림됩니다.
+ 예시 :
    + Math.ceil(5.05)는 6을 반환합니다.
    + Math.ceil(-5.05)는 -5를 반환합니다.

### Math.round()
주어진 숫자를 가장 가까운 정수로 반올림합니다. 소수점 이하 값이 0.5 이상이면 올림하고, 0.5 미만이면 내립니다.
+ 예시 :
    + Math.round(5.5)는 6을 반환합니다.
    + Math.round(5.4)는 5를 반환합니다.

### Math.trunc()
주어진 숫자의 소수 부분을 버립니다. 즉, 소수점 이하를 제거하고 정수 부분만 남깁니다. 양수인 경우에는 그냥 내림하고, 음수인 경우에는 그냥 올립니다.
+ 예시 :
    + Math.trunc(5.95)는 5를 반환합니다.
    + Math.trunc(-5.95)는 -5를 반환합니다.

이제 저희는 정수를 반환하는 방법을 알았습니다.
저희는 저 4가지 함수중 가장 마지막인 Math.trunc()을 사용하겠습니다.

이유는 예시에서 7 나누기 2 를 했을때 원래의 값은 3.5 지만 출력을 해야하는 값은 3이여야 합니다.
Math.floor()을 사용하게 되면 만약 코드 테스트에서 음수를 사용하면 값이 달라지고,
Math.ceil()을 사용하게 되면 값을 올려버려 값이 달라지게 됩니다.
마찬가지로 Math.round()을 사용하게 되면 Math.floor()와 마찬가지로 음수의 값이 변하게 됩니다.

위와 같은 이유로 정수의 위치가 변하지 않고 소수점을 전부 버리는 Math.trunc()을 사용하도록 하겠습니다.

이제 코드에 적용해보겠습니다.
```javascript
function solution(num1, num2) {
    var answer = Math.trunc(num1/num2);
    return answer;
}
console.log(solution(7, 2))
``` 

이제 결과값이 3으로 정상 출력 되었습니다.
문제에서 원하는 정수값만 나오게 되는 함수를 만들었으니
이제 이 코드를 [프로그래머스](https://programmers.co.kr/)에서 확인해보겠습니다.

![프로그래머스 이미지](../assets/img/몫구하기_03.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '몫 구하기' 문제의 대해서 알아봤습니다.

감사합니다.
