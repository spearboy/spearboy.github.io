---
layout: post
title: 프로그래머스 LV1 "음양 더하기"
date: 2024-05-04 15:02 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv1 음양 더하기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 열여섯번째 문제 '음양 더하기' 문제입니다.

  ![프로그래머스 이미지](/assets/img/음양더하기_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 `absolutes`와 `signs`가 주어지면 `signs`안에 있는 `boolean`값을 이용해 `absolutes`의 수를 음수나 양수로 변환해 모든 값을 합해 출력하는 문제 입니다.

  오늘 문제에서는 간단한 반복문과 조건문으로 문제를 해결해 보겠습니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.

```javascript
function solution(absolutes, signs) {
  var answer = 123456789;
  return answer;
}
```

기본 세팅 코드는 매개변수 `absolutes`는 숫자가 담긴 배열의 형태로 입력되고, `signs`는 `boolean`값이 담긴 배열을 입력해주며 함수 안에는 `answer`이라는 변수가 선언되어 리턴되는 간단한 기본 세팅 코드입니다.

우선 오늘의 문제의 핵심을 알아보겠습니다. 문제의 핵심은 예를 들어 `absolutes`의 값이 `[1,2,3,4,5]`이고 `signs`의 값이 `[true,false,true,true,false]`이면 `absolutes`값은 `[1,-2,3,4,-5]`가 될것입니다. 그럼 이 값들을 다 합한 값이면 1임으로 리턴 값은 1이 되어야 합니다.

이렇게 문제의 핵심을 잠시 설명 드렸습니다. 그렇다면 문제의 답을 먼저 보여드리고 코드를 살펴보겠습니다.

```javascript
function solution(absolutes, signs) {
  var answer = 0;
  absolutes.forEach((e,index) => {
    if(signs[index] == true){
      answer+= e;
    }else {
      answer+= -e;
    }
  })
  return answer;
}
```

위 코드가 문제의 풀이 입니다. 제 포스팅을 많이 보셨던 분이라면 코드를 보시면 이해를 하셨을거라 생각합니다.

간단하게 코드에 대한 설명을 요약해보겠습니다.

1. 변수 초기화: 우선, 결과값을 저장할 변수 `answer`를 0으로 초기화합니다.

2. 배열 순회: `absolutes` 배열의 각 요소에 대해 `forEach` 반복문을 실행합니다. 이 반복문은 배열의 각 요소를 순차적으로 처리합니다.

3. 조건문: `forEach` 반복문 내부에서는 `signs` 배열의 동일한 인덱스 위치에 있는 요소를 확인하여 조건문을 통해 해당 숫자를 더할지 뺄지 결정합니다.   만약 `signs[index]`가 `true`라면 해당 숫자를 그대로 더합니다.   
만약 `signs[index]`가 `false`라면 해당 숫자를 음수로 처리하여 더합니다.

5. 결과 반환: 최종적으로 계산된 `answer` 값을 반환합니다.

이렇게 코드를 작성함으로써, `solution` 함수는 `absolutes` 배열과 `signs` 배열을 인자로 받아서 각 숫자를 더하거나 빼서 최종 결과값을 반환합니다.

이렇게 코드에 대한 요약을 해보았습니다.

그럼 프로그래머스에 제출하기 위해 다시 코드를 확인해보겠습니다.

```javascript
function solution(absolutes, signs) {
  var answer = 0;
  absolutes.forEach((e,index) => {
    if(signs[index] == true){
      answer+= e;
    }else {
      answer+= -e;
    }
  })
  return answer;
}
```

문제의 식이 완성되었으니 프로그래머스에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/음양더하기_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '문자열 내림차순으로 배치하기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.