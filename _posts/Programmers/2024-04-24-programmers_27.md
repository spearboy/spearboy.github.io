---
layout: post
title: 프로그래머스 LV1 "나머지가 1이 되는 수 찾기"
date: 2024-04-24 21:23 +0900
description: 
image: ../assets/img/programmers_logo.png
category: [programmers, Lv1]
tags: code lv1 programmers javascript
published: true
sitemap: true
---

# 프로그래머스 Lv1 나머지가 1이 되는 수 찾기

  기초부터 다시 공부를 하기위해 [프로그래머스](https://programmers.co.kr/) 라는 사이트에서
  코딩테스트를 LV0 부터 가능한곳까지 못하는곳은 레퍼런스를 찾아가며 풀어보려고 합니다.
  
  매일 1개의 풀이를 하고 그 풀이에대한 나의 생각 및 해석을 적어보려합니다.

  오늘은 LV1 일곱번째 문제 '나머지가 1이 되는 수 찾기' 문제입니다.

  ![프로그래머스 이미지](https://spearboy.github.io/assets/img/나머지가1이되는수찾기_01.png)

  위 이미지가 프로그래머스 코딩문제입니다.
  
  문제는 매개변수로 정수 `n`이 주어지면 `n`이하의 자연수중 나머지가 1인 자연수를 반환하는 문제입니다.

  오늘 문제에서는 간단한 반복문과 "반복문 제어 구문" 사용해 해결해 보겠습니다.

  그럼 오늘의 문제를 한번 풀어보겠습니다.

  기본 세팅 코드도 알아보겠습니다.
  
```javascript
function solution(n) {
  var answer = 0;
  return answer;
}
```

기본 세팅코드는 간단하게 정수 `n` 매개변수를 전달하며 함수안에 있는 `answer`변수에 정수 0이 리턴되는 기본적인 함수의 형태입니다.

우선 문제의 메커니즘을 한번 알아보겠습니다. 입출력 예 설명에 보시면

`n`이 10이면 3 이고,`n`이 12이면 11입니다.

`n`이 10이면 3인 이유는 아래와 같습니다.
10을 이하의 자연수로 나머지 연산했을때
10 % 1 = 0   
10 % 2 = 0   
10 % 3 = 1   
10 % 4 = 2   
10 % 5 = 0   
10 % 6 = 4   
10 % 7 = 3   
10 % 8 = 2   
10 % 9 = 1   
10 % 10 = 0   
위에서 보시는것과 같이 나머지연산시 자연수들의 값이 나열이 됩니다. 하지만 문제에서 1이 될 수 있는 가장 작은 자연수를 리턴해 달라고 했으니 보시는 바와 같이 나머지 연산이 1이 되는 제일 작은 자연수는 3 입니다.

그럼 `n`이 12이면 11인 이유도 한번 알아보겠습니다.
12를 이하의 자연수로 나머지 연산했을때
12 % 1 = 0   
12 % 2 = 0   
12 % 3 = 0   
12 % 4 = 0   
12 % 5 = 2   
12 % 6 = 0   
12 % 7 = 5   
12 % 8 = 4   
12 % 9 = 3   
12 % 10 = 2   
12 % 11 = 1   
12 % 12 = 0   
위에서 보시는것과 같이 나머지연산시 자연수들의 값이 나열이 됩니다. 12는 1이 될 수 있는 가장 작은 자연수가 11입니다.

이렇게 입출력 예시의 결과가 왜 3과 11이 나오는지 설명 드렸습니다.

위에 보시는것과 같이 모든 수를 비교하려면 간단하게 반복문을 사용하면 될것입니다.

```javascript
function solution(n) {
  var answer = 0;
  for(let i = 1; i<=n; i++ ){
    if(n%i == 1 ){
      answer = i;
      break;
    }
  }
  return answer;
}
```
이렇게 반복문 이용했습니다. 중간에 처음 보시는 `break`라는게 있습니다. 여기서 오늘 처음에 말했던 "반복문 제어 구문"에 대해서 한번 알아보고 겠습니다.

## 반복문 제어 구문

오늘 설명드릴 3가지 "반복문 제어 구문"입니다. 

### return
return 문은 현재 함수를 종료하고 값을 반환합니다. 반복문 내에서 사용될 때, 해당 반복문의 실행을 중지하고 함수를 종료합니다.

```javascript
function func(numbers) {
  for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] == 3) {
      return
    }
    console.log(numbers[i]);
  }
}

const Array = [1, 2, 3, 4, 5];
func(Array); // 출력: 1, 2
```

### continue
현재 반복을 중지하고 다음 반복으로 넘어갑니다. 주로 특정 조건을 만족할 때 현재 반복 단계를 건너뛸 때 사용됩니다.

```javascript
function func(numbers) {
  for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] == 3) {
      continue
    }
    console.log(numbers[i]);
  }
}

const Array = [1, 2, 3, 4, 5];
func(Array); // 출력: 1, 2, 4, 5
```

### break
반복문을 중지하고 반복문을 빠져나옵니다. 주로 특정 조건이 충족되면 반복문을 종료할 때 사용됩니다.

```javascript
function func(numbers) {
  for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] == 3) {
      break
    }
    console.log(numbers[i]);
  }
}

const Array = [1, 2, 3, 4, 5];
func(Array); // 출력: 1, 2
```

이렇게 3가지 "반복문 제어 구문"을 알아보았습니다.

그럼 코드에 대해 이어서 설명을 드리겠습니다.

```javascript
function solution(n) {
  var answer = 0;
  for(let i = 1; i<=n; i++ ){
    if(n%i == 1 ){
      answer = i;
      break;
    }
  }
  return answer;
}
```
보시는것과 같이 나머지가 1이 되는 숫자를 찾으면 `break`를 사용하여 반복문을 종료하는 함수를 만들어 주었습니다. 이렇게 되면 나머지가 1이 되는 숫자중 가장 작은 수를 반환 하는 식이 만들어 졌습니다.

완성된 코드를 다시 한번 보여드리겠습니다.

```javascript
function solution(n) {
  var answer = 0;
  for(let i = 1; i<=n; i++ ){
    if(n%i == 1 ){
      answer = i;
      break;
    }
  }
  return answer;
}
```

문제의 식이 완성되었으니 프로그래머스에 한번 확인해보겠습니다.

![프로그래머스 이미지](https://spearboy.github.io/assets/img/나머지가1이되는수찾기_02.png)

성공이네요!

오늘은 [프로그래머스](https://programmers.co.kr/) LV1 '평균 구하기' 문제의 대해서 알아봤습니다.

제 방법이 꼭 정답은 아니니 그저 이런방법도 있구나하고 참고용으로만 봐주시면 감사하겠습니다.

감사합니다.