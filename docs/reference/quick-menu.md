# 빠른 메뉴 영역 참고 자료 (2026-11-24 원본 기준)

> 출처 표시: **🟢 화면 측정** · **🟡 원본 HTML/CSS 파일만 확인** · **⬜ 측정 필요**
> 구조는 원본 HTML(🟡), 크기·색은 브라우저 화면 측정(🟢)이에요.

## 생김새

제목 "완벽한 여행 준비를 위한 **구석구석 서비스**" 아래에 아이콘 + 글자 메뉴 9개가 한 줄로 놓여요. 모바일에서는 가로로 밀어서 넘겨요 (HTML 주석 기준).

## 원본 구조 (🟡 원본 HTML, 클래스 이름은 원본 그대로)

```
div.main_quick_nav                 ← 빠른 메뉴 전체
├ h3  "완벽한 여행 준비를 위한 <strong>구석구석 서비스</strong>"
└ div.swiper
  └ div.swiper-wrapper
    └ div.swiper-slide (×9)        ← 메뉴 1개
      └ a
        ├ span.icon > img          ← 아이콘 이미지
        └ strong                   ← 메뉴 이름
```

## 메뉴 순서와 아이콘 파일 (🟡 원본 HTML)

| 순서 | 메뉴 이름 | 원본 아이콘 파일 |
| --- | --- | --- |
| 1 | 디지털관광주민증 | `main_quick_menu7.png` |
| 2 | 대한민국 반값여행 | `main_quick_menu9.png` |
| 3 | 지역 인기 음식점 | `main_quick_menu2.png` |
| 4 | 가볼래-터 | `main_quick_menu3.png` |
| 5 | 배지랜드 | `main_quick_menu4.png` |
| 6 | 축제달력 | `main_quick_menu5.png` |
| 7 | 여행코스 | `main_quick_menu1.png` |
| 8 | 여행상품 | `main_quick_menu6.png` |
| 9 | 여행가이드북 | `main_quick_menu8.png` |

- 우리 HTML은 `assets/images/main_quick_menu○.png`를 가리키고 있어요. **이미지 파일은 아직 없어요.** 원본에서 내려받아 넣어 주세요.

## 측정값 (🟢 2026-11-24 화면 측정 · 창 너비 1864px · `html` 글자 크기 10px)

> 소수점 값은 원본 CSS(main.css)에서 **작성된 값**을 찾아 계산이 화면 측정값과 맞는지 확인했어요. CSS에는 **원본 작성값**을 쓰세요.

| 요소 | 속성 | 값 |
| --- | --- | --- |
| 영역 전체 `.main_quick_nav` | 너비 / 최대 너비 | 1280px / 1280px (가운데 정렬) |
|  | `margin-top` | 62px |
|  | `padding-bottom` | 72px |
| 제목 `h3` | `font-size` / `line-height` | 26px / 33.8px → **원본 작성값 `130%`** (26 × 1.3 = 33.8) |
|  | `font-weight` | 400 |
|  | `letter-spacing` | -0.52px → **원본 작성값 `-0.02em`** (26 × -0.02 = -0.52) |
|  | `color` | rgb(41, 41, 44) = #29292c |
| 제목 강조 `strong` | `font-weight` | 800 (색·크기는 h3와 같음) |
| 슬라이드 전체 `.swiper` | `padding-top` (제목과 메뉴 사이) | 32px |
|  | `overflow` | hidden |
| 메뉴 묶음 `.swiper-wrapper` | `display` | flex |
| 메뉴 1개 `.swiper-slide` | 너비 | 122px |
|  | 높이 | 125.6 → **지정값 없음, 내용으로 정해짐** (아이콘 88 + 간격 16 + 이름 줄 높이 21.6) |
|  | 메뉴 사이 간격 | 22.75px (`margin-right`) — ⏸️ **원본 CSS에 없음, Swiper가 계산해서 넣는 값** |
| 링크 `a` | `display` / `flex-direction` / `align-items` | flex / column / center |
| 아이콘 `span.icon` | 크기 | 88 × 88 |
|  | `border-radius` | 36px |
|  | `box-shadow` | 0 0 6px rgba(26, 26, 26, 0.15) |
|  | 배경색 | 없음 (투명) |
|  | `display` | flex |
| 아이콘 이미지 `img` | 크기 | 60 × 60 → **원본 작성값 `width: 60px; height: auto`** (정사각형 이미지라 높이도 60) |
| 메뉴 이름 `strong` | `font-size` / `line-height` | 18px / 21.6px → **원본 작성값 `120%`** (18 × 1.2 = 21.6) |
|  | `font-weight` | 600 |
|  | `letter-spacing` | -0.9px → **원본 작성값 `-0.05em`** (18 × -0.05 = -0.9) |
|  | `color` | rgb(41, 41, 44) = #29292c |
|  | `padding-top` (아이콘과의 간격) | 16px |

- 9개 메뉴가 1280px 너비에 딱 맞게 놓여요 (마지막 메뉴 오른쪽 끝 = 1280px).

## 반복되는 값 → 토큰 후보

| 값 | 쓰인 곳 | 토큰 (`css/tokens.css`) |
| --- | --- | --- |
| #29292c | 제목, 메뉴 이름 | `--color-text` (이미 있음) |
| 1280px | 영역 최대 너비 | `--layout-max` (이미 있음) |
| 600 / 800 | 메뉴 이름 / 제목 강조 굵기 | `--fw-semibold` / `--fw-extrabold` (이미 있음) |
| 1.3 (130%) | 제목 줄 간격 — 원본은 메인의 **모든 h3**에 같은 값 | `--lh-title` (새로 추가) |
| 1.2 (120%) | 메뉴 이름 줄 간격 | `--lh-tight` (이미 있음) |
| -0.02em | 제목 자간 | `--ls-base` (이미 있음) |
| 16px · 32px | 아이콘↔이름 간격 · 제목↔메뉴 간격 | `--space-4` · `--space-8` (이미 있음) |
| 18px · 26px · 62px · 72px · 88px · 60px · 36px | 이 영역에서 처음 나온 값 | 다른 영역에서 반복되면 토큰으로 추가 제안 |

## 움직임 (JavaScript 단계에서 사용)

- 모바일에서 가로 슬라이드 (Swiper) — ⬜ 원본에서 관찰 필요
- 클릭하면 각 서비스 페이지로 이동 (원본은 클릭 기록을 남기는 함수를 거쳐 이동)

## 이 영역에서 배우는 CSS

| 개념 | 어디에 쓰나 | 📖 MDN |
| --- | --- | --- |
| flex (복습), gap | 메뉴 9개 가로 나열, 아이콘·글자 세로 배치 | [gap](https://developer.mozilla.org/ko/docs/Web/CSS/gap) |
| flex-direction: column | 아이콘 위, 글자 아래 | [flex-direction](https://developer.mozilla.org/ko/docs/Web/CSS/flex-direction) |
| 같은 클래스 재사용 | 메뉴 9개에 같은 규칙 | — |
