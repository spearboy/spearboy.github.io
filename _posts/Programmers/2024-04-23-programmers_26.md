---
layout: post
title: 프로그래머스 LV1 "평균 구하기"
date: 2024-04-23 18:10 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv1 평균 구하기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 여섯번째 문제 '평균 구하기' 문제입니다.

  ![프로그래머스 이미지](/assets/img/평균구하기_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 `arr`이 주어지면 `arr`의 요소들의 평균을 구하는 간단한 문제입니다. 오늘은 쉬어가는 문제가 될거같습니다.   
  (이번 포스팅은 조금 짧게 끝날거같습니다...)

  오늘 문제에서는 간단한 반복문을 사용해 해결해 보겠습니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(arr) {
  var answer = 0;
  return answer;
}
```

기본 세팅코드는 간단하게 `arr`라는 배열 형태의 매개변수를 전달하며 함수안에 있는 `answer`변수에 정수 0이 리턴되는 기본적인 함수의 형태입니다.

우선 문제의 핵심은 주어진 배열의 모든 요소를 더하여 그 값을 배열의 수만큼 나누면 평균이 나올것 입니다.

그렇다면 배열을 모두 합하려면 지금까지 많이 써왔던 반복문으로 처리를 하면 될것입니다.

그럼 코드로 한번 제가 말한것들을 옮겨보겠습니다.

```javascript
function solution(arr) {
  var answer = 0;
  var total = 0;
  for(let i=0; i<arr.length; i++){
    total += arr[i];
  }
  answer = total/arr.length;
  return answer;
}
```

위 코드에 대한 설명을 간단하게 하겠습니다.

우선 `total`이라는 변수를 생성했습니다. 저 변수는 모든 요소의 합이 될것입니다.

바로 다음에 반복문으로 매개변수로 입력된 `arr`의 길이만큼 반복하면 `arr`의 `i`번째 요소를 `total`에 더해주고 있습니다.
결과적으로 `total`은 모든 요소의 합이 될것입니다.

바로 다음 `answer`변수에 `total`을 `arr`의`length`값 만큼 나누어 주었습니다.

이렇게 매개변수로 들어오는 `arr`요소들의 평균값을 구할 수 있게 되었습니다.

완성된 코드를 다시 한번 보여드리겠습니다.

```javascript
function solution(arr) {
  var answer = 0;
  var total = 0;
  for(let i=0; i<arr.length; i++){
    total += arr[i];
  }
  answer = total/arr.length;
  return answer;
}
```

문제의 식이 완성되었으니 프로그래머스에 한번 확인해보겠습니다.

![프로그래머스 이미지](/assets/img/평균구하기_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '평균 구하기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.