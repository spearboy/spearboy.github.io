---
layout: post
title: scroll
date: 2024-06-02 12:27 +0900
description: 
image: ../assets/img/css_fun.gif
category: [code, css]
tags: code css scroll
published: true
sitemap: true
---

# 오직 css만으로 스크롤 애니메이션을 만들어보자

오늘은 최근 제가 알게된 좀 좋은? 무튼 스크롤과 관련된 신규 css속성을 소개해 드려볼까 합니다.

우선 처음으로는 `Scroll Snap`입니다.

## CSS Scroll Snap

CSS Scroll Snap은 웹 개발자가 웹 페이지의 스크롤 동작을 조절할 수 있는 CSS 속성입니다. 이 기능은 사용자가 스크롤할 때 스크롤 위치를 지정된 지점에 "스냅"시켜 자연스럽고 부드러운 스크롤 경험을 제공합니다.

### 1. `scroll-snap-type`

`scroll-snap-type` 속성은 스크롤 컨테이너에서 스크롤 스냅을 사용할지 여부를 설정합니다. 이 속성은 다음과 같은 값으로 설정될 수 있습니다:

- `scroll-snap-type: none;`: 스크롤 스냅을 사용하지 않습니다.
- `scroll-snap-type: x mandatory;`: x축으로 스크롤 스냅을 사용하며, 스크롤을 움직일 때 항상 스냅 지점에 정렬됩니다.
- `scroll-snap-type: y mandatory;`: y축으로 스크롤 스냅을 사용하며, 스크롤을 움직일 때 항상 스냅 지점에 정렬됩니다.
- `scroll-snap-type: both mandatory;`: x축과 y축 모두에 대해 스크롤 스냅을 사용하며, 스크롤을 움직일 때 항상 스냅 지점에 정렬됩니다.

### 2. `scroll-snap-align`

`scroll-snap-align` 속성은 요소가 스냅 지점에 정렬될 때의 동작을 설정합니다. 이 속성은 다음과 같은 값으로 설정될 수 있습니다:

- `scroll-snap-align: none;`: 스냅 지점에 정렬되지 않습니다.
- `scroll-snap-align: start;`: 요소를 스냅 지점의 시작 부분에 정렬합니다.
- `scroll-snap-align: center;`: 요소를 스냅 지점의 중앙에 정렬합니다.
- `scroll-snap-align: end;`: 요소를 스냅 지점의 끝 부분에 정렬합니다.

### 3. 주의사항

- `scroll-snap-type` 및 `scroll-snap-align` 속성은 일부 브라우저에서 아직 완전히 지원되지 않을 수 있습니다. 따라서 사용할 때에는 브라우저 호환성을 고려해야 합니다.
- 스크롤 스냅은 터치 기반 디바이스와 마우스 모두에서 작동하지만, 터치 기반 디바이스에서 더 자연스러운 사용자 경험을 제공합니다.

CSS Scroll Snap은 갤러리, 이미지 슬라이더, 캐러셀 및 페이지 매김과 같은 요소들을 구현할 때 유용하게 사용될 수 있습니다. 사용자는 스크롤을 통해 요소들 사이를 자유롭게 이동할 수 있으면서도 요소들이 지정된 위치에 자연스럽게 스냅되는 경험을 얻을 수 있습니다.

위 설명처럼 꼭 js으로 스크롤 위치값과 잡다한 값 등등을 구하고 비교하지 않아도 또 특별한 라이브러리를 사용하지 않아도 스크롤 기능을 구현할 수 있다니 매력적이지 않을 수 없습니다! 그럼 제 코드펜에서 예제를 확인해 보겠습니다.

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="gOJmjNL" data-pen-title="scroll snap (scroll css)" data-user="_Babo_" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/_Babo_/pen/gOJmjNL">
  scroll snap (scroll css)</a> by alex (<a href="https://codepen.io/_Babo_">@_Babo_</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>