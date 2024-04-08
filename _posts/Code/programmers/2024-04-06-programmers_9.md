---
layout: post
title: 프로그래머스 LV0 "문자열 뒤집기"
date: 2024-04-06 17:19 +0900
description: 
image: ../assets/img/programmers_logo.png
category: code
tags: code lv0 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv0 문자열 뒤집기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 아홉번째 문제 '문자열 뒤집기' 문제입니다.

  ![프로그래머스 이미지](../assets/img/문자열뒤집기_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수'numbers'에 문자열을 전달 하면 해당 문자열을 거꾸로 출력하는 문제입니다.

  이번문제에서는 반복문과 배열에 관련된 함수들을 사용해보겠습니다.

  이제 기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(my_string) {
    var answer = 0;

    return answer;
}
``` 
기존과 같은 기본 함수의 형태입니다. 이번엔 함수에서 `my_string` 이라는 문자열을 매개변수로 입력하고 있습니다.

우선 저는 함수에 제가 필요한 변수를 추가로 생성하고 사용하기 쉽게 `answer`변수에 매개변수를 담아주겠습니다.

```javascript
function solution(my_string) {
    var answer = my_string;
    var revers = [];
    var newString = '';

    return answer;
}
``` 
그리고 저는 문제풀이를 위한 빈 배열과 빈 문자열을 가지고있는 변수 두개를 만들었습니다.

여기서 문제풀이를 시작할때 말했던 배열에 관련된 함수를 잠시 알아보고 문제 풀이를 이어가보도록 하겠습니다.

### 배열 메서드 or 배열 함수
JavaScript에서 "배열 메서드" 또는 "배열 함수"라고 불립니다. 이들 함수는 배열을 조작하고 변환하는 데 사용됩니다. 일부는 배열의 요소를 추가, 제거, 변경하고, 다른 일부는 배열을 새로운 형태로 변환하거나 조작합니다.

#### push()
+ 배열의 끝에 하나 이상의 요소를 추가합니다.
  + 예시
    + ```javascript
      let fruits = ['apple', 'banana'];
      fruits.push('orange');
      // fruits = ['apple', 'banana', 'orange']
      ```
#### pop()
+ 배열의 마지막 요소를 제거하고 반환합니다.
  + 예시
    + ```javascript
      let fruits = ['apple', 'banana', 'orange'];
      let removedFruit = fruits.pop();
      // removedFruit = 'orange', fruits = ['apple', 'banana']
      ```
#### shift()
+ 배열의 첫 번째 요소를 제거하고 반환합니다.
  + 예시
    + ```javascript
      let fruits = ['apple', 'banana', 'orange'];
      let removedFruit = fruits.shift();
      // removedFruit = 'apple', fruits = ['banana', 'orange']
      ```
#### unshift()
+ 배열의 시작 부분에 하나 이상의 요소를 추가합니다.
  + 예시
    + ```javascript
      let fruits = ['banana', 'orange'];
      fruits.unshift('apple');
      // fruits = ['apple', 'banana', 'orange']
      ```
#### split()
+ 문자열을 지정된 구분자를 기준으로 나누어 배열로 변환합니다.
  + 예시
    + ```javascript
      let sentence = 'Hello, world!';
      let words = sentence.split(' ');
      // words = ['Hello,', 'world!']
      ```

이렇게 배열함수의 일부분을 알아보았습니다. 기타 배열함수는 다음 포스팅에서 다뤄보도록 하겠습니다.

이제 저는 `my_string`의 문자열 분리를 위해 `split()` 사용해서 콘솔에 값을 알아보겠습니다.

```javascript
function solution(my_string) {
    var answer = my_string.split("");
    var revers = [];
    var newString = '';

    return answer;
}
console.log(solution("apple"))
``` 

결과값은 `['a', 'p', 'p', 'l', 'e']`으로 문자열이 한글자씩 분리되어 배열의 형태로 반환되었습니다.
그럼 이제 이 배열의 각각의 문자를 `revers`라는 빈 배열에 다시 추가 해보도록 하겠습니다.
여기서 저희는 추가하는 2개의 매서드인 `push()`와`unshift()` 중 배열의 앞에 추가하는`unshift()` 매서드를 사용해보겠습니다.
추가하는 방법은 반복문을 이용하면 간단하게 추가가 가능합니다.

```javascript
function solution(my_string) {
    var answer = my_string.split("");
    var revers = [];
    var newString = '';
    
    for(let i = 0; i<answer.length; i++){
        revers.unshift(answer[i]);
    }

    return revers;
}
console.log(solution("apple"))
``` 

위코드처럼 반복문으로 `split()`을 사용해 배열로 반환된 `answer`의`length`값 만큼 루프를 돌리는 반복문안에
매 루프마다 `answer[i]`를 `unshift()`으로 `revers`에 추가 하고 있습니다.   
이번에는 리턴값을 `revers`으로 변경해 콘솔을 출력해보았습니다.

결과값은 `['e', 'l', 'p', 'p', 'a']`, 성공적으로 문자열의 순서가 거꾸로 들어갔습니다.

이제 남은건 배열에서 각 값을 가져와 빈 문자열 변수인 `newString`에 추가해주면 되겠습니다.
이번에도 쉽게 반복문으로 해결해보겠습니다.

```javascript
function solution(my_string) {
    var answer = my_string.split("");
    var revers = [];
    var newString = '';
    
    for(let i = 0; i<answer.length; i++){
        revers.unshift(answer[i]);
    }
    for(let i = 0; i<revers.length; i++){
        newString = newString + revers[i];
    }

    answer = newString;
    return answer;
}
console.log(solution("apple"))
``` 

두번째 반복문은 배열인 `revers`의`length`값 만큼 루프를 돌리는 반복문안에
매 루프마다 `revers[i]`를 연산자`+`으로 `newString`에 추가 하고 있습니다.
루프가 끝나면 이제 `answer`에 다시 `newString`을 할당하여 리턴값을 다시 `answer`으로 돌려주었습니다.
이제 모든 함수가 완성되었으니 결과값을 한번 출력해보겠습니다. 저는 매개변수에 "apple" 이라는 문자열을 넣어주었습니다.
그럼 위함수가 정상적으로 작동이 된다면 콘솔에는 "elppa" 가 출력 될것입니다.   
   
결과는 "elppa". 성공적으로 문자열을 뒤집어서 출력했습니다.

이제 원하는 결과가 나오고 함수가 원하는대로 작동하니 프로그래머스에서 결과를 확인해 보겠습니다.

```javascript
function solution(my_string) {
    var answer = my_string.split("");
    var revers = [];
    var newString = '';
    
    for(let i = 0; i<answer.length; i++){
        revers.unshift(answer[i]);
    }
    for(let i = 0; i<revers.length; i++){
        newString = newString + revers[i];
    }

    answer = newString;
    return answer;
}
``` 
제출용으로 정리한 코드는 위와 같습니다.

![프로그래머스 이미지](../assets/img/문자열뒤집기_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV0 '문자열 뒤집기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.