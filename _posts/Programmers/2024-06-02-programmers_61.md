---
layout: post
title: 오직 css만으로 스크롤 애니메이션을 만들어보자
date: 2024-06-02 12:27 +0900
description: 
image: 
category: [code, css]
tags: code css scroll
published: true
sitemap: true
---

# 오직 css만으로 스크롤 애니메이션을 만들어보자

![프로그래머스 이미지](/assets/img/css_fun.gif)

오늘은 최근 제가 알게된 좀 좋은? 무튼 스크롤과 관련된 신규 css속성을 소개해 드려볼까 합니다.

저는 스냅이나 스크롤 위치에 따른 동적 애니메이션 등 이런 기능을 사용하려고 `javascript`라이브러리 혹은 스크립트를 직접 만들거나 했습니다. 그런 제가 불쌍할 정도로 간편하고 매력적인 기능인거같습니다. 한번 같이 확인해 보겠습니다.

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

<iframe height="300" style="width: 100%;" scrolling="no" title="scroll snap (scroll css)" src="https://codepen.io/_Babo_/embed/gOJmjNL?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/_Babo_/pen/gOJmjNL">
  scroll snap (scroll css)</a> by alex (<a href="https://codepen.io/_Babo_">@_Babo_</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

위 코드 처럼 저희는 이렇게 스냅을 `javascript`없이 구현할 수 있습니다! 정말 간편하군요..

`javascript`으로만 저 예제를 구현하려면... 상상만해도 귀찮네요ㅎㅎ..

그럼 이렇게 css 스냅을 알아보았습니다.

그럼 다음으로 이번 포스팅의 메인 하이라이트인 `animation-timeline`관련 기능들을 알아보도록 하겠습니다.

## CSS animation-timeline
여러분은 알고계셨나요 이 속성하나로 스크롤 애니메이션이 된다는것을?.....

~~Holy fuck~~

CSS animation-timeline에서 사용되는 `scroll()` 및 `view()` 함수는 `CSS` 애니메이션을 특정 요소의 스크롤이나 화면에 대한 가시성에 따라 트리거하는 데 사용됩니다.

- `scroll()` 함수: 이 함수는 요소의 스크롤 위치에 따라 애니메이션을 트리거합니다. 즉, 사용자가 페이지를 스크롤하면 해당 요소에 지정된 애니메이션이 발생합니다. 이를 통해 페이지 스크롤에 반응하는 동적인 효과를 만들 수 있습니다.

- `view()` 함수: `view()` 함수는 요소의 화면 내 가시성에 따라 애니메이션을 트리거합니다. 예를 들어, 요소가 화면에 들어오거나 화면을 벗어날 때 애니메이션이 발생하도록 설정할 수 있습니다. 이는 요소가 사용자의 눈에 보이거나 사라질 때 애니메이션을 추가하여 사용자 경험을 향상시키는 데 유용합니다.


애니메이션을 트리거하고 제어하기 위한 다양한 속성이 포함되어 있습니다. 여기에는 `animation-range-start`와 `animation-range-end`뿐만 아니라 `animation-timeline`, `animation-range`도 포함됩니다.

- `animation-timeline`: 이 속성은 애니메이션을 트리거할 이벤트를 정의합니다. 여기서는 일반적으로 `scroll()`이나 `view()`와 같은 함수를 사용합니다. 이 함수들은 스크롤이나 요소의 가시성에 따라 애니메이션을 트리거합니다.

- `animation-range`: 애니메이션을 활성화할 범위를 지정합니다. `entry`나 `exit`와 같은 값으로 설정하여 요소가 페이지의 뷰포트에 진입하거나 벗어날 때 애니메이션이 시작되도록 할 수 있습니다.

- `animation-range-start`: 애니메이션이 시작되는 위치를 정의합니다. 일반적으로 `entry`나 `exit`와 같은 값을 가집니다. 요소가 페이지의 뷰포트에 진입할 때 또는 뷰포트를 벗어날 때 애니메이션이 시작되도록 설정할 수 있습니다.

- `animation-range-end`: 애니메이션이 끝나는 위치를 정의합니다. 이 역시 `entry`나 `exit`와 같은 값을 가집니다. 요소가 페이지의 뷰포트에 진입하거나 벗어날 때 애니메이션이 종료되도록 설정할 수 있습니다.

이러한 속성들을 조합하여 요소의 애니메이션을 세밀하게 제어할 수 있습니다. 요소의 출현 및 사라짐, 스크롤 등의 동작에 반응하여 애니메이션이 발생하도록 조정할 수 있습니다. 이는 사용자 경험을 개선하고 동적인 웹페이지를 구현하는 데 유용합니다.

이러한 함수들을 사용하여 요소들이 페이지의 특정 상황에 반응하고, 이에 따라 동적인 애니메이션을 생성할 수 있습니다.

말이 더 필요할까요? 그냥 예시 코드를 보여드리겠습니다. 우선 `scroll()`함수를 사용한 전체 페이지 스크롤바입니다.

<iframe height="300" style="width: 100%;" scrolling="no" title="scroll watcher(use scroll bar)" src="https://codepen.io/_Babo_/embed/mdYWjGe?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/_Babo_/pen/mdYWjGe">
  scroll watcher(use scroll bar)</a> by alex (<a href="https://codepen.io/_Babo_">@_Babo_</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

정말 간편하지 않습니까? 만약 저걸 `js`으로 구현하려면 전체 페이지의 스크롤값 - 현재 스크롤 위치를 계산하고 어쩌구 저쩌구....

귀-찮-습-니-다

하지만 위코드는 그런 계산이 필요가 없습니다. 그냥 애니메이션 안에서 설정만 해주면 끝입니다.



그럼 다음으로 `view()` 를 한번 알아보겠습니다.

<iframe height="300" style="width: 100%;" scrolling="no" title="Untitled" src="https://codepen.io/_Babo_/embed/RwOEYxp?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/_Babo_/pen/RwOEYxp">
  Untitled</a> by alex (<a href="https://codepen.io/_Babo_">@_Babo_</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

위 코드는 **뷰포트**를 감지하여 애니메이션을 **트리거**하는 코드입니다.

위 코드처럼 만드는것도 쉽겠지만 보시는바와 같이 css 하나로 이렇게 구현이 된다면 제 생각은 불필요한 js를 더 줄일 수 있겠다 라는 생각이 들더라구요.

오늘은 간단하게 `scroll`으로 작동할 수 있는 `css animation` 을 알아보았습니다. 

감사합니다.