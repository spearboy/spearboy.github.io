---
layout: post
title: 프로그래머스 LV1 "문자열 내 p와 y의 개수"
date: 2024-04-18 22:24 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv1 문자열 내 p와 y의 개수

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  지금까지 LV0의 20개의 문제를 풀어보았습니다. 오늘부터는 레벨을 올려서 LV1문제로 달려가 보겠습니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 첫번째 문제 '문자열 내 p와 y의 개수' 문제입니다.

  ![프로그래머스 이미지](/assets/img/p와y의갯수_01.jpg)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 문자열`s`가 주어지면 문자열 내에 `p`와 `y`의 갯수가 같으면 `true`를 틀리면 `false`를 출력해야하는 문제입니다.

  그럼 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(s){
  var answer = true;
  return answer;
}
``` 
  지금까지의 기본함수와 같은 형태의 기본 함수입니다.
  그럼 바로 코드를 우선 문자열의 길이를 알아야하닌 `length`를 사용해 길이를 알아보겠습니다.

### length

  javascript에서 `length`는 배열이나 문자열에 포함된 요소의 개수를 나타냅니다. 다음은 각각의 사용 방법에 대한 간단한 설명입니다

  1. 배열에서 `length`

  ```javascript
  const fruits = ['apple', 'banana', 'orange'];
  console.log(fruits.length); // 출력: 3

  fruits.push('grape'); // 배열에 요소를 추가
  console.log(fruits.length); // 출력: 4

  fruits.pop(); // 배열의 마지막 요소를 삭제
  console.log(fruits.length); // 출력: 3
  ```

  2. 문자열에서 `length`

  ```javascript
  const str = 'Hello, World!';
  console.log(str.length); // 출력: 13
  ```

  이렇게 `length`에대해 알아보았습니다.

  그럼 한번 반복문을 이용해 문자열을 을 확인해 보겠습니다.
  ```javascript
  function solution(s){
    var answer = "";
    
    for(let i = 0; i<s.length; i++){
        answer+=s[i];
    }

    return answer;
  }
  ```
  위코드와 같이 각문자열의 `index`위치의 문자열을 `answer`에 넣어주었습니다. 반복문을 이용해 각 문자를 가져올 수 있게 되었습니다. 그럼 해당 문자가 `p`인지, `y`인지 구분을 해야합니다. 간단하게 조건문으로 코드의 나머지 부분을 작성해 보겠습니다.

  ```javascript
  function solution(s){
    var answer = "";
    let yNum = 0;
    let pNum = 0;
    for(let i = 0; i<s.length; i++){
        if(s[i] == "p") {
            pNum++;
        }else if (s[i] == "y") {
            yNum++;
        }
    }
    if(yNum == pNum) {
        answer = true;
    }else {
        answer = false;
    }
    
    return answer;
  }
  ```
  위 코드에서 저는 `p`의 갯수를 `pNum`이라는 변수에 담아주고 `y`의 갯수는 `yNum`이라는 변수에 저장하고있습니다. 마지막 조건문에서는 `pNum`와`yNum`의 수가 같으면 `answer`에 `true`를 담아 리턴해주고, 같지 않다면 `false`를 리턴해주고 있습니다.

  얼핏 보기에 코드가 완성된거같지만 한가지 부족한게 있습니다.

  바로 대소문자를 전부 판별하는게 아니라 현재는 소문자만 판별하는것입니다. 이번 문제에서는 문자열의 대문자를 소문자로 바꿔주는 메서드인 `toLowerCase()`라는 메서드를 알아보겠습니다.
  
### toLowerCase()

  문자열을 소문자로 변환하는 메서드는 `toLowerCase()`입니다. 이 메서드는 대문자를 소문자로 변경합니다.

  예시   
  ```javascript
  const str = "Hello, World!";
  const lowerCaseStr = str.toLowerCase();
  console.log(lowerCaseStr); // 출력: "hello, world!"
  ```

  그럼 `toLowerCase()`를 사용해 코드를 수정을 해보겠습니다.

  ```javascript
  function solution(s){
    var answer = "";
    let yNum = 0;
    let pNum = 0;
    let sLow = s.toLowerCase()
    for(let i = 0; i<sLow.length; i++){
        if(sLow[i] == "p") {
            pNum++;
        }else if (sLow[i] == "y") {
            yNum++;
        }
    }
    if(yNum == pNum) {
        answer = true;
    }else {
        answer = false;
    }
    
    return answer;
  }
  ```
  위 코드에서는 `sLow`라는 변수에 `s`문자열을 `toLowerCase()`메서드를 이용해 소문자로 바꿔주고 `sLow`을 사용해 `p`와`y`의 갯수를 카운트하는 반복문으로 바꿨습니다.

  그럼 코드가 완성 되었으니 한번 프로그래머스에서 결과를 확인해 보겠습니다.

![프로그래머스 이미지](/assets/img/p와y의갯수_02.jpg)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '문자열 내 p와 y의 개수' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.