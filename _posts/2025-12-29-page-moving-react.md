---
title: 사용자 페이지 이동 감지 기능
description: performance api 
date: 2025-12-29 09:30:00
categories: [Develop, Web]
tags: [develop, web]     # TAG names should always be lowercase
---

# 사용자 페이지 이동 감지

## Performance API의 활용

> 홈페이지 정책상, 테스트 진행 중간에 데이터를 저장하지 않는 경우, 페이지 이동 / 새로고침 / 뒤로가기 등으로 **데이터가 누적·왜곡되는 상황을 방지해야 함**


⇒ 이를 위해 **클라이언트 단에서 “페이지 진입 방식”을 판단하는 로직**이 필요하여 그 중 하나로 **Performance API**를 활용하였습니다. 

---

## 1.  Performance API

> 웹 애플리케이션의 성능 지표를 수집·측정하기 위한 브라우저 API
> 
- 브라우저가 **로드 / 렌더링 / 입력 / 리소스 요청** 등을 측정
- 모든 성능 데이터는 **PerformanceEntry** 객체로 표현됨
- 각 엔트리는 `entryType`(문자열) 속성을 가짐

---

### 1.1 getEntriesByType()

> 지정한 entryType에 해당하는 PerformanceEntry들을 "배열" 형태로 반환
> 

**`performance.getEntriesByType(type)`**

### - 주요 entryType 종류

1. `"element"`
- 특정 DOM 요소가 **로드·렌더링**되는 데 걸린 시간
1. `"event"`
- 이벤트 발생 → 핸들러 실행까지의 지연 시간
- INP(Interaction to Next Paint) 측정에 사용
1. `"first-input"`
- 첫 사용자 입력 지연(FID)
1. `"largest-contentful-paint"`
- LCP (가장 큰 콘텐츠가 그려진 시점)
1. `"layout-shift"`
- CLS (레이아웃 이동량)
1. `"longtask"`
- 50ms 이상 걸린 작업 기록
1. `"mark"`
- 개발자가 직접 찍은 타임스탬프
1. `"measure"`
- mark 사이의 사용자 정의 측정값
1. `"paint"`
- first-paint, first-contentful-paint
1. `"resource"`
- 이미지, JS, CSS 등 리소스 로딩 시간
- PerformanceResourceTiming 객체
1. `"visibility-state"`
- 탭이 foreground ↔ background로 바뀐 시점
1. `"navigation"`
- **페이지 탐색 및 초기 로드 정보**
- PerformanceNavigationTiming 객체 반환

---

### 1.2 entryType별 누적 특성

```jsx
// 여러 개 누적됨
resource / mark / measure
// 문서 단위 1개
navigation             

//navigation은 항상 “현재 문서 기준 단일 엔트리” 따라서 배열의 인덱스 0을 사용한다.
performance.getEntriesByType("navigation")[0];
```

**주의**) performance.getEntriesByType("navigation")  1번 인덱스는 존재하지 않음

---

## 2. navigation.type 으로 페이지 진입 방식 판별

```jsx
const nav = performance.getEntriesByType("navigation")[0];
// 에러 처리 코드 넣을 것 
if (!nav) return; 

if (nav.type ==="reload" || nav.type ==="back_forward") {
// 새로고침 또는 뒤/앞 이동 코드 시 사용할 코드 입력
}
```

### `PerformanceNavigationTiming.type` 값

![img](https://tnosh7.github.io/assets/img/functions/pageMove1.png)

| 값 | 의미 |
| --- | --- |
| `"navigate"` | 일반 진입 (URL 직접 입력, 링크 클릭) |
| `"reload"` | 새로고침 |
| `"back_forward"` | 브라우저 뒤로/앞 이동 |
| `"prerender"` | 미리 로딩 |

![img](https://tnosh7.github.io/assets/img/functions/pageMove2.png)

참고) [https://developer.mozilla.org/en-US/docs/Web/API/PerformanceNavigationTiming/type](https://developer.mozilla.org/en-US/docs/Web/API/PerformanceNavigationTiming/type)

## 참고) performance.navigation 을 권장하지 않는 이유

**`performance.navigation`** 

### 1. 문제점

- 숫자 enum 에서 가독성 낮음
- SPA 환경과 맞지 않음
- 모바일 / Safari / WebView에서 값 신뢰도 낮음
- 확장 불가능 (표준 폐기)

⇒ 현재 표준은 Navigation Timing

---
