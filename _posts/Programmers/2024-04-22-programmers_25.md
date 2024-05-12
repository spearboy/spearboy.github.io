---
layout: post
title: 프로그래머스 LV1 "자연수 뒤집어 배열로 만들기"
date: 2024-04-22 21:43 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv1 자연수 뒤집어 배열로 만들기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 다섯번째 문제 '자연수 뒤집어 배열로 만들기' 문제입니다.

  ![프로그래머스 이미지](../assets/img/자연수뒤집어배열로만들기_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 정수 `n`이 주어지면 `n`의 각 자릿수를 뒤집어 `answer`에 추가해 배열의 형태로 출력하는 문제입니다.

  오늘 문제에서는 간단한 반복문과 이전 포스팅에서 사용했던 `Number()`내장함수와 `String()`내장함수, 그리고 `unshift()`를 사용해서 문제를 해결해 보겠습니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(n) {
  var answer = [];
  return answer;
}
```

기본 세팅코드는 간단하게 `n`라는 매개변수를 전달하며 함수안에 있는 `answer`변수에 빈 배열이 리턴되는 기본적인 함수의 형태입니다.

오늘은 문제를 풀기전에 `unshift()`메서드에 대해 한번 알아보고 문제를 해결해 보겠습니다.
추가로 `Number()`와 `String()`내장함수는 이전 포스팅인 [프로그래머스 Lv1 문자열을 정수로 바꾸기](https://spearboy.github.io/posts/programmers_22/),[프로그래머스 Lv1 자릿수 더하기](https://spearboy.github.io/posts/programmers_24/)포스팅에서 확인 가능합니다.

그럼 시작 전에 이전에 LV0 포스팅중에 [프로그래머스 Lv0 문자열 뒤집기](https://spearboy.github.io/posts/programmers_9/)에서 한번 설명했었던 `unshift()`를 한번 간단하게 설명드리고 문제풀이를 진행해 보겠습니다.

### unshift()

`unshift()` 메서드는 JavaScript 배열의 맨 앞에 하나 이상의 요소를 추가하는 데 사용됩니다. 이 메서드는 배열의 길이를 변경하고, 새로운 요소들을 배열의 시작 부분에 추가합니다.
  + 반환값: `unshift()` 메서드는 새로운 배열의 길이를 반환합니다. 이 값은 배열에 추가된 새로운 요소의 개수와 같습니다.
  + 원본 배열 수정: `unshift()` 메서드는 호출된 배열을 수정하고, 새로운 배열을 생성하지 않습니다. 따라서 기존 배열에 직접 요소들을 추가합니다.
  + 요소 추가: `unshift()` 메서드는 인자로 전달된 요소들을 배열의 맨 앞에 추가합니다. 여러 개의 요소를 동시에 추가할 수 있으며, 전달된 순서대로 배열의 맨 앞에 추가됩니다.
  + 배열의 길이: 요소가 추가될 때마다 배열의 길이가 증가합니다. `unshift()`를 호출할 때마다 배열의 길이가 변경됩니다.

다음은 `unshift()` 메서드를 사용하는 예시입니다.
```javascript
let arr = [3, 4, 5];
console.log(arr.unshift(1, 2)); // 출력: 5 (새로운 배열의 길이)
console.log(arr); // 출력: [1, 2, 3, 4, 5]

let newArr = [];
console.log(newArr.unshift("a", "b", "c")); // 출력: 3 (새로운 배열의 길이)
console.log(newArr); // 출력: ["a", "b", "c"]
```

위의 예시에서 첫 번째 배열 arr에는 이미 [3, 4, 5]가 있었고, `unshift()`를 호출하여 맨 앞에 1과 2를 추가했습니다. 두 번째 배열 `newArr`는 초기에 비어 있었고, `unshift()`를 호출하여 "a", "b", "c"를 추가했습니다.

이렇게 `unshift()`에 대해 한번 알아 보았습니다.

그럼 문제를 한번 해결해 보도록 하겠습니다.

```javascript
function solution(n) {
  var answer = [];
  var num = String(n);
  return answer;
}
```

우선 저는 숫자인 매개변수 `n`을 변수`num`안에 문자열로 바꾸어 담아주었습니다. 바꾼 문자열의 `length`값을 가져오기 위해서 입니다.

```javascript
function solution(n) {
  var answer = [];
  var num = String(n);
  for(let i= 0; i< num.length; i++){
    answer.unshift(Number(num[i]))
  }
  return answer;
}
```

간단한 `for()`반복문으로 `num`의 `length`값 만큼 반복문을 돌리며 그 안에는 `unshift()`으로 배열의 첫번째에 추가를 해주고있습니다. `unshift()`를 사용함으로서 문자열의 `i`번째의 값을 다시 `Number()`으로 숫자로 바꾸면서 `answer`안에 첫번째 요소로 추가를 해주면 순서는 `1`,`2,1`,`3,2,1`,`4,3,2,1`이렇게 입렵될것입니다.

그럼 문제의 주요 포인트인 자연수를 뒤집는것과 해당 자연수를 배열에 담는것이 완성 되었습니다.

완성된 코드를 한번 보여드리겠습니다.

```javascript
function solution(n) {
  var answer = [];
  var num = String(n);
  for(let i= 0; i< num.length; i++){
    answer.unshift(Number(num[i]))
  }
  return answer;
}
```

문제의 식이 완성되었으니 프로그래머스에 한번 확인해보겠습니다.

![프로그래머스 이미지](../assets/img/자연수뒤집어배열로만들기_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '자연수 뒤집어 배열로 만들기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.