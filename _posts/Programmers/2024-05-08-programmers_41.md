---
layout: post
title: 프로그래머스 LV2 "최댓값과 최솟값"
date: 2024-05-08 23:12 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv2]
tags: code lv2 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv2 최댓값과 최솟값

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.

  지금까지 LV0의 20개,LV1의 20개 문제를 풀어보았습니다. 오늘부터는 레벨을 올려서 LV2문제로 달려가 보겠습니다.

  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV2 첫번째 문제 '최댓값과 최솟값' 문제입니다.

  ![프로그래머스 이미지](/assets/img//post41_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 문자열 `s`를 입력받아 문자열 중 최소값과 최대값을 문자열로 출력하는 문제입니다.

  오늘 문제는 첫 LV2인 만큼 조금 가벼운 문제로 골라 보았습니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(s) {
    var answer = '';
    return answer;
}
```

기본 세팅 코드는 매개변수 `s`문자열이 입력되고 함수 안에는 `answer`이라는 변수가 선언되어 빈 문자열을 리턴하는 간단한 기본 세팅 코드입니다.

우선 문자열 `s`는 공백으로 구분된 여러개의 숫자를 가지고있습니다. 각 숫자를 구분하기 위해 문자열의 `length`를 이용하거나 `index`를 활용할 수 있습니다.

하지만 그렇게 처리를하면 복잡한 과정이 될 수 있습니다. 따라서 오늘 문제는 `Math.min()`과 `Math.max()`함수로 해결을 해보겠습니다.

우선 문자열이 공백으로 구분되어있다고 합니다. 그럼 공백을 기준으로 분리를 하면 될것입니다. 여기서 저는 `split()`을 사용해 문자열을 배열로 만들겠습니다.

```javascript
function solution(s) {
    var answer = s.split(" ");
    return answer;
}
console.log(solution("1 2 3 4 5 6 7 8 9 10"))
```

위 코드의 결과는 `['1', '2', '3', '4', '5', '6', '7', '8', '9', '10']`으로 출력 될것입니다.

이 배열에서 `Math.min()`과 `Math.max()`를 사용해 최소값과 최대값을 구하면 문제는 해결이 될것입니다.

이전 문제에서 사용했었지만 제가 설명을 안드렸던것이 한가지 있습니다. 바로 '확산 연산자'입니다.
그럼 간단하게 한번 알아보고 문제를 마무리 하겠습니다.

## 확산 연산자(Spread Operator)

`...`은 `JavaScript`의 확산 연산자(Spread Operator)입니다. 이 연산자는 배열이나 객체를 확장하거나 병합할 때 사용됩니다.

1. 배열 확장:
확산 연산자를 사용하여 배열을 다른 배열에 추가하거나 병합할 수 있습니다. 예를 들어, `[1, 2, ...[3, 4], 5]`와 같이 사용하면 `[1, 2, 3, 4, 5]`와 같은 배열이 생성됩니다.

2. 함수 호출:
함수를 호출할 때 배열의 요소를 인수로 전달할 수 있습니다. 예를 들어, `myFunction(...myArray)`와 같이 사용하면 배열 `myArray`의 각 요소가 함수 `myFunction`에 전달됩니다.

3. 객체 확장:
확산 연산자를 사용하여 객체를 다른 객체에 병합할 수 있습니다. 예를 들어, `{ ...obj1, ...obj2 }`와 같이 사용하면 `obj1`과 `obj2`의 속성이 병합된 새로운 객체가 생성됩니다.

이러한 방식으로 확산 연산자는 코드를 간결하게 작성하고 가독성을 높이는 데 도움이 됩니다.

이렇게 확산 연산자에 대해서 한번 알아 보았습니다.

그럼 확산 연산자를 이용해 한번 문제를 마무리 해보겠습니다. 코드는 간단합니다.

```javascript
function solution(s) {
    var answer = s.split(" ");
    answer = Math.min(...answer)+" "+Math.max(...answer);
    return answer;
}
```

문제의 식이 완성되었으니 프로그래머스에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img//post41_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV2 '최댓값과 최솟값' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.