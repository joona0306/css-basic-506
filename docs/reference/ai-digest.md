# AI 기사 요약 · 사용자 후기 영역 참고 자료 (2026-11-24 원본 기준)

> 출처 표시: **🟢 화면 측정** (창 너비 1864px · `html` 글자 크기 10px) · **🟡 원본 CSS 파일** · **⬜ 측정 필요**
> 소수점 값은 원본 CSS(main.css)의 **작성값**을 찾아 계산이 맞는지 확인했어요. CSS에는 작성값을 쓰세요.

## 생김새

```
[AI가 지금 막, 여행기사ㆍ사용자 후기를 요약했어요.] (i)   ← 제목 + 정보 버튼
(<)                                                (>)   ← 이전·다음 원형 버튼 (카드 높이 가운데쯤)
┌────────────┐ ┌────────────┐ ┌────────────┐
│[여행기사]   │ │[사용자 후기]│ │ …          │   ← 파란 이름표(카드 위쪽에 붙음)
│(●) 제목 2줄 │ │(●) 제목     │ │            │   ← 동그란 사진 + 파란 제목
│────────────│ │────────────│ │            │   ← 얇은 구분선
│ 요약 6줄    │ │ 요약 6줄    │ │            │
│[바로가기]   │ │[바로가기]   │ │            │
└────────────┘ └────────────┘ └────────────┘
               ━ ● ● ● ●                         ← 점 모양 페이지 표시
```

- 영역 배경: 연한 파란 그라데이션 + 오른쪽 장식 이미지 (`assets/images/bg_ai_digest.png`, 프로젝트에 이미 있음)
- 카드 15장 (여행기사 9 · 사용자 후기 6, 섞여 있음). 우리는 정지 화면용으로 **3장**만 만들어요.
- 제목 옆 (i) 버튼을 누르면 설명 말풍선(툴팁)이 열려요 → JS 단계.

## 원본 구조 (🟡 원본 HTML, 클래스 이름은 원본 그대로)

```
div.ai_digest                          ← 영역 전체
├ div.tit_wrap                         ← 제목 줄
│ ├ h3 "AI가 지금 막, <strong>여행기사ㆍ사용자 후기를 요약했어요.</strong>"
│ ├ button.icon_pg_info_md             ← (i) 정보 버튼
│ └ div.wrap_layerpop.ui_pg_tooltip    ← 설명 말풍선 (평소 숨김)
│   └ div.layerpop > div.cont (strong.stit + p) ×2, button.close
└ div.swiper
  ├ div.swiper-wrapper
  │ └ div.swiper-slide (×15)
  │   └ div.cont                       ← 카드
  │     ├ em (span 아이콘 + "여행기사" / "사용자 후기")   ← 파란 이름표
  │     ├ div.tit > strong             ← 제목
  │     ├ p                            ← 요약
  │     ├ span.thumbs > img            ← 동그란 사진
  │     └ a.btn_pg_xs > span "바로가기"
  ├ div.page_btn                       ← 이전·다음 버튼 묶음
  │ ├ div.swiper-button-prev > button > span(아이콘)
  │ └ div.swiper-button-next > button > span(아이콘)
  └ div.swiper-pagination              ← 점 모양 페이지 표시 (점은 Swiper가 만듦)
```

## 측정값

### 영역과 제목

| 요소 | 속성 | 값 | 출처 |
| --- | --- | --- | --- |
| 영역 `.ai_digest` | 위 안쪽 여백 | 87px (`8.7rem`) | 🟢 |
|  | 위 바깥 여백 | 0 (원본 CSS는 72px이지만 빠른 메뉴 바로 다음이라 `0 !important`로 덮어써짐) | 🟢 |
|  | 배경 | `bg_ai_digest.png`를 가운데 기준 오른쪽(`calc(50% + 29rem) 0`)에 한 번 + `linear-gradient(180deg, #E9F0FE 0%, rgba(242, 246, 255, 0.6) 123.06%)` | 🟡 |
| 제목 줄 `.tit_wrap` | 너비 · 가운데 정렬 | 1280px, 좌우 auto | 🟢 |
|  | 배치 | flex, 세로 가운데, `gap` 12px | 🟢 |
| 제목 `h3` | 글자 | 26px · 줄 간격 **`130%`** · 자간 **`-0.02em`** · 굵기 400 · #29292c | 🟢 (빠른 메뉴 제목과 같음) |
| 제목 강조 `strong` | 굵기 | 800 | 🟢 |
| 정보 버튼 | 크기 | 20 × 20 | 🟢 |

### 카드

| 요소 | 속성 | 값 | 출처 |
| --- | --- | --- | --- |
| 슬라이드 `.swiper` | 안쪽 여백 | 위 37px · 아래 86px | 🟢 |
| 카드 칸 `.swiper-slide` | 너비 × 높이 | 410px × 376px | 🟢 |
|  | 카드 사이 | 24px — ⏸️ Swiper 설정값 | 🟢 |
| 카드 `.cont` | 안쪽 여백 | 위 52px · 좌우 36px · 아래 0 | 🟢 |
|  | 배경 / 모서리 | #fff / 20px | 🟢 |
|  | 그림자 | `0 0 20px #D0DBF0` | 🟢 |
|  | `position` / `overflow` | relative / hidden | 🟢🟡 |
| 이름표 `em` | 위치 | absolute, 카드 왼쪽 36px · 위 0 | 🟢 |
|  | 배치 | inline-flex, 세로 가운데, `gap` 4px, 좌우 안쪽 여백 8px | 🟢 |
|  | 높이 | 32px | 🟢 |
|  | 글자 | 14px · 굵기 700 · 흰색 · 기울임 없음 | 🟢 |
|  | 배경 | #236CF6 (원본 변수 `--brand-primary-50`) | 🟢 |
|  | 모서리 | 아래 두 곳만 4px (`0 0 4px 4px`) | 🟢 |
| 이름표 아이콘 | 크기 | 16 × 16 | 🟢 |
| 동그란 사진 `.thumbs` | 위치 | absolute, 왼쪽 36px · 위 52px | 🟢 |
|  | 크기 / 모서리 | 52 × 52 / 100% / `overflow: hidden` | 🟢 |
| 사진 `img` | 크기 / 맞춤 | 100% × 100% / `object-fit: cover` | 🟢 |
| 제목 칸 `.tit` | 배치 | flex, 세로 가운데, 높이 52px | 🟢 |
|  | 왼쪽 바깥 여백 | 68px (사진 52 + 간격 16) | 🟢 |
| 제목 `strong` | 글자 | 20px · 줄 간격 26px (`2.6rem`) · 굵기 600 · 자간 **`-0.05em`** (= -1px) | 🟢 |
|  | 색 | #236CF6 | 🟢 |
|  | 2줄 넘으면 말줄임 | `-webkit-line-clamp: 2` | 🟢 |
| 요약 `p` | 위 바깥 / 안쪽 여백 | 20px / 17px | 🟢 |
|  | 윗줄 | `1px solid #E9E9F4` | 🟢 |
|  | 글자 | 16px · 줄 간격 24px · 자간 **`-0.02em`** (= -0.32px) · #58585F | 🟢 |
|  | 높이 | 144px (24px × 6줄, 원본 작성값 `14.4rem`) — 화면에서는 여백·선 포함 162 | 🟢🟡 |
|  | 6줄 넘으면 말줄임 | `-webkit-line-clamp: 6` | 🟢 |
| 바로가기 `a` | 위치 | absolute, 왼쪽 36px · 아래 36px | 🟢 |
|  | 크기 / 배치 | 높이 32px, 좌우 안쪽 여백 12px, flex | 🟢 |
|  | 글자 | 14px · 굵기 700 · #29292c | 🟢 |
|  | 배경 / 모서리 | #F3F3FA / 50px | 🟢 |

### 이전·다음 버튼과 페이지 표시

| 요소 | 속성 | 값 | 출처 |
| --- | --- | --- | --- |
| 버튼 묶음 `.page_btn` | 위치 | absolute, 1280px 너비, 위 226px | 🟢 (⏸️ Swiper 배치와 함께) |
| 이전 / 다음 칸 | 크기 · 위치 | 40 × 40, 왼쪽 -19px / 오른쪽 -19px | 🟢 |
| 버튼 `button` | 모양 | 흰 배경, `1px solid #949499`, 모서리 100% | 🟢 |
| 점 묶음 `.swiper-pagination` | 위치 / 배치 | 아래 50px / flex 가운데, `gap` 8px | 🟢 |
| 점 (보통) | 크기 · 색 · 모서리 | 8 × 8 · #8E8E8E · 50% | 🟢 (⏸️ 점은 Swiper가 만듦) |
| 점 (현재) | 크기 · 색 · 모서리 | 16 × 8 · #3D3D43 · 50px | 🟢 (⏸️) |

## 반복되는 값 → 토큰 후보

| 값 | 쓰인 곳 | 토큰 |
| --- | --- | --- |
| #236CF6 | 이름표 배경, 카드 제목 (원본 `--brand-primary-50`) | `--color-primary` (새로 추가 제안) |
| #29292c, 1280px, 130%, -0.02em, -0.05em(빠른 메뉴와 같음) | 제목, 버튼 글자 | 이미 있는 토큰 / 같은 값 반복 |
| 800, 700, 600 | 굵기 | `--fw-extrabold` 있음, 700은 새 값 |
| 14px · 16px · 20px | 글자 크기 | `--fs-sm` · `--fs-base` · `--fs-lg` (이미 있음) |
| 32px | 이름표·바로가기 높이 | `--space-8`과 같은 값 |

## 움직임 (JavaScript 단계에서 사용)

- 카드 15장 슬라이드 (Swiper), 이전·다음 버튼, 점 모양 페이지 표시
- (i) 버튼을 누르면 설명 말풍선 열기 / 닫기 버튼
- 카드에 마우스를 올리면 카드 테두리가 3px 파란색으로 0.5초 동안 바뀜 (`::after` + transition) → 5·6단계

## 이 영역에서 배우는 CSS

| 개념 | 어디에 쓰나 | 📖 MDN |
| --- | --- | --- |
| 배경 여러 겹 (이미지 + 그라데이션) | 영역 배경 | [background](https://developer.mozilla.org/ko/docs/Web/CSS/background) · [linear-gradient()](https://developer.mozilla.org/ko/docs/Web/CSS/gradient/linear-gradient) |
| position (복습) | 이름표, 사진, 바로가기 | [position](https://developer.mozilla.org/ko/docs/Web/CSS/position) |
| 여러 줄 말줄임 | 제목 2줄, 요약 6줄 | [-webkit-line-clamp](https://developer.mozilla.org/ko/docs/Web/CSS/-webkit-line-clamp) |
| 모서리 따로 둥글게 | 이름표 아래쪽만 | [border-radius](https://developer.mozilla.org/ko/docs/Web/CSS/border-radius) |
