# SlideHeader

모든 본문 장의 머리: 섹션 라벨(왼쪽 위) · 페이지 번호(오른쪽 위) · 헤드라인 · 리드. 덱의 2~30장이 같은 좌표를 쓴다.

## 배치 규칙
- 섹션 라벨 `.qw-label section-label`: x=`margin-x`(80) y=`label-y`(56), `brand`. 장 이름은 대표 표기 그대로("CHAPTER 1 · WEEK 2~7", "CORE PHILOSOPHY"). 1줄, 최장 40자(25장 "CHAPTER 3 · FINAL  PRESENTATION & AWARDS").
- 페이지 번호 `.qw-pagenum body-24-eb`: 오른끝 x=1840 y=`pagenum-y`(67), `gray-500`, 두 자리("04").
- 헤드라인 `.qw-headline headline`: y=`headline-y`(125), `ink`. 1~2줄, 1줄 최장 28자(6장 "기다리지 않고, 직접 움직이고, 빠르게 판매합니다."). 더 길면 `title-42`(10장, 2줄 40자).
- 리드 `.qw-lead lead`: y=`lead-y`(217), `gray-600`, 1줄 최장 55자. 본문은 `content-y`(288)부터.
- 강조 런은 `<span class="qw-hl">`(brand). 헤드라인 안 강조는 한 구절만(11·23·28장).

## 변형
- 사진 장 `.qw-slide--photo`: 라벨·번호·헤드라인·리드 모두 `on-brand`, 헤드라인·리드에 `shadow-text-50`. 라벨 굵기는 700이 기본, 16장만 500.
- 그라데이션 장 `.qw-slide--gradient`(6·14장, Backgrounds/blue-gradient.jpeg): 전부 흰 글자, 그림자 없음.
- 검정 장 `.qw-slide--dark`(8장, Backgrounds/dark-blue-glow.png): 라벨은 `yellow`, 나머지 흰 글자.

## 소비자가 주는 것
라벨 문자열, 페이지 번호, 헤드라인(강조 구절 포함), 리드. 배경 변형 클래스 하나.
