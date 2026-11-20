# 히어로 영역 참고 자료 (2026-11-20 원본 사이트 기준)

> 원본 사이트를 브라우저 화면 너비 1864px에서 열고, 개발자 도구로 **실제로 측정한 값**이에요.
> 원본 사이트는 내용이 자주 바뀌니, 다르게 보이면 개발자 도구로 다시 확인하세요.

## 생김새

```
┌──────┐ ┌──────────────────────────────┐ ┌──────┐
│ 이전  │ │        큰 사진 (카드)          │ │ 다음  │
│ 카드  │(<)                            (>) 카드  │
│ 일부  │ │ 제목 (2줄, 굵게, 흰색)         │ │ 일부  │
│      │ │ 부제목 (흐린 흰색)             │ │      │
│      │ │ [자세히 보기 >]       2 / 10 ⏸ │ │      │
└──────┘ └──────────────────────────────┘ └──────┘
```

- 가운데 큰 카드 1장 + 양옆 카드가 **조금씩** 보이는 모양이에요.
- 슬라이드는 모두 10장이에요. (넘기는 동작은 JavaScript라서 우리는 **정지 화면**만 만들어요.)
- 예전에 만든 HTML 구조(캠페인 이름, 날짜, 버튼 2개, 작은 이미지 슬라이드)는 **지금 사이트에 없어요.**

## 원본 구조 (클래스 이름은 원본 그대로)

```
div.main_showcase_area            ← 히어로 전체
└ div.swiper                      ← 슬라이드 묶음
  ├ div.swiper-wrapper            ← 카드들을 가로로 나열
  │ └ div.swiper-slide (×10)      ← 카드 1장
  │   ├ span.img > img            ← 사진
  │   └ a                         ← 글자 묶음 (링크)
  │     ├ strong                  ← 제목
  │     ├ em                      ← 부제목
  │     └ span.view               ← "자세히 보기 >" 버튼 모양
  ├ div.nav_btn                   ← 이전 / 다음 화살표 버튼
  └ div.page_btn                  ← "2 / 10" 숫자 + 일시정지 버튼
```

> 우리 프로젝트는 **케밥 케이스**를 쓰니, 클래스 이름은 직접 바꿔서 지어요. (예: `hero`, `hero-slide` …)

## 측정값

| 요소 | 속성 | 값 |
| --- | --- | --- |
| 카드 1장 | width × height | 940px × 626px |
|  | 카드 사이 간격 | 16px (오른쪽 margin) |
|  | border-radius | 12px |
|  | overflow | hidden (사진이 둥근 모서리 밖으로 안 나가게) |
|  | position | relative (글자 묶음의 기준 상자) |
| 사진 `img` | 크기 | 카드와 같음 (940 × 626) |
|  | object-fit | cover |
| 글자 묶음 `a` | position | absolute |
|  | left / bottom | 48px / 48px |
|  | width | 630px |
| 제목 `strong` | font-size / weight / line-height | 40px / 800 / 48px |
|  | color | #fff |
| 부제목 `em` | font-size / weight | 20px / 400 |
|  | color | rgba(255, 255, 255, 0.75) |
|  | font-style | normal (em의 기본 기울임을 없앰) |
| "자세히 보기" | display | inline-flex |
|  | font-size / 높이 | 14px / 32px |
|  | padding | 0 16px |
|  | border | 1px solid rgba(255, 255, 255, 0.5) |
|  | border-radius | 2px |
| 이전·다음 버튼 | 크기 | 56px × 56px 원 |
|  | background-color | rgba(0, 0, 0, 0.4) |
| "2 / 10" + 일시정지 | 위치 | 카드 오른쪽 아래 |

## 이 영역에서 배우는 CSS

| 개념 | 어디에 쓰나 | 📖 MDN |
| --- | --- | --- |
| position (복습) | 카드 = 기준 상자, 글자 묶음 = absolute | [position](https://developer.mozilla.org/ko/docs/Web/CSS/position) |
| overflow | 둥근 모서리 밖으로 나가는 사진 자르기, 양옆 카드 자르기 | [overflow](https://developer.mozilla.org/ko/docs/Web/CSS/overflow) |
| border-radius | 카드 모서리, 원형 버튼 | [border-radius](https://developer.mozilla.org/ko/docs/Web/CSS/border-radius) |
| object-fit | 사진이 찌그러지지 않게 채우기 | [object-fit](https://developer.mozilla.org/ko/docs/Web/CSS/object-fit) |
| rgba 색 | 반투명 글자·테두리·버튼 배경 | [rgb()](https://developer.mozilla.org/ko/docs/Web/CSS/color_value/rgb) |
| flex (복습) | 카드 3장 가로 나열, 버튼 안 글자+아이콘 | [flexbox](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox) |

## 이미지

- 원본 슬라이드 사진은 프로젝트에 없어요. 지금은 `assets/images/hero_img_1_1.png`, `hero_img_1_2.png` 같은 **있는 이미지로 대신** 써요.
- 원본 사진이 꼭 필요하면 직접 내려받아 `assets/images/`에 넣으세요.
