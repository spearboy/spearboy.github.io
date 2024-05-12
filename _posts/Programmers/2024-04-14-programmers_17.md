---
layout: post
title: 프로그래머스 LV0 "중앙값 구하기"
date: 2024-04-14 21:55 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv0]
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv0 중앙값 구하기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 열일곱번째 문제 '중앙값 구하기' 문제입니다.

  ![프로그래머스 이미지](../assets/img/중앙값구하기_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수 `array`이 주어지면 `array`안에 숫자들을 순서대로 정렬후 중간에 있는 숫자를 출력하는 문제입니다.

  이번문제에서도 메서드중 하나인 `sort()`를 사용해서 한번 문제를 풀어보도록 하겠습니다.

  이제 기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(array) {
  var answer = 0;
  return answer;
}
``` 
기존과 같은 기본 함수의 형태입니다. 이번엔 함수에서 `array`라는 매개변수를 입력하고 있습니다. 그리고 이 매개변수는 배열의 형태로 주어지고 있습니다.

우선 오늘 사용해볼 `sort()`메서드에 대해서 간단하게 설명을 드리겠습니다.

### sort() 
`sort()`는 JavaScript 배열을 정렬하는 함수입니다. 숫자 배열의 경우 `sort((a, b) => a - b)`와 같이 사용하여 오름차순으로 정렬할 수 있고, 문자열 배열의 경우는 그냥 `sort()`를 호출하면 알파벳순으로 정렬됩니다.

+ 예시 : 숫자 정렬(오름차순)
  + ```javascript
      let test = [6,4,7,1,5,2];
      test.sort((a,b) => a - b);
      // 결과 [1,2,4,5,6,7]
    ```

+ 예시 : 숫자 정렬(내림차순)
  + ```javascript
      let test = [6,4,7,1,5,2];
      test.sort((a,b) => b - a);
      // 결과 [7,6,5,4,2,1]
    ```
이렇게 숫자의 경우 이런 형태의 정렬이 실행됩니다.

이번에는 문자열의 `sort()`입니다.

+ 예시 : 문자 정렬(오름차순)
  + ```javascript
      let test = ['apple','car','ball'];
      test.sort();
      // 결과 ['apple','ball','car']
    ```

+ 예시 : 숫자 정렬(내림차순)
  + ```javascript
      let test = ['apple','car','ball'];
      test.sort().reverse();
      // 결과 ['car','ball','apple']
    ```
문자열의 경우 오름차순은 그냥 메서드를 호출하면 정렬이 됩니다.
반대로 내림차순의 경우에는 `reverse()`메서드를 사용하지만 오늘은 `reverse()`메서드에 대해서는 설명하지 않고 다음에 다시 포스팅 하겠습니다.

이렇게 정렬하는 메서드를 활용해서 우선 `array`에 주어지는 배열을 작은수에서 큰수 순서대로 정렬해야하니 오름차순으로 정렬해보겠습니다.

```javascript
function solution(array) {
  var answer = 0;

  answer = array.sort((a,b) => a - b);

  return answer;
}
``` 
잠시 출력 결과인 `answer`에 정렬이 잘 되었는지 확인을 위해 정렬된 배열을 담아서 확인해보았습니다. 결과는 오름차순으로 잘 나오는것을 확인했습니다.

이제 중간수를 구해야합니다. 간단히 생각해보면 2로 나눈값을 출력하면 될거같습니다. 하지만 javascript의 나누기는 소수점까지 출력함으로 정수로 변환해주는 메서드중 `Math.trunc()`를 사용하여 정수로 반환해주겠습니다.

```javascript
function solution(array) {
  var answer = 0;

  array.sort((a,b) => a - b);

  let mid = Math.trunc(array.length/2);

  answer = array[mid];

  return answer;
}
``` 
저는 `mid`라는 변수안에 중간 값을 저장했습니다. 그리고 `mid`으로 `array`의 중간 `index`를 선택해 `answer`에 담아 출력해주었습니다.
이제 코드가 완성 되었으니 한번 프로그래머스에서 결과를 확인해 보겠습니다.

![프로그래머스 이미지](../assets/img/중앙값구하기_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '중앙값 구하기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.