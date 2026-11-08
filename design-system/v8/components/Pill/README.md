# Pill

덱의 알약·배지·탭. 모두 `radius-pill`(완전한 알약)이고 높이와 색만 다르다. 글자는 가운데, 좌우 여백 `pill-pad-x`(24).

## 변형(장 → 클래스)
- 4장 "목표": `--solid` brand/on-brand, 높이 50, `label-26`(700). 4장 "방해물": `--outline` 흰 2px 테두리(사진 위).
- 6장 카드 모서리 "추운 겨울": `--tint` brand-200/navy, 높이 50, `body-24-eb`(700). 21장 "8W – 16W": 같은 알약 116×52에 `body-20-bold`(brand).
- 17장 "CPF/PSF/SPF": `--yellow`(yellow/orange-deep) · `--tint-sm`(brand-200/brand) · `--solid-sm`(brand/on-brand), 높이 46, `body-16-bold`. 단계 완료 색 규칙: 지난 단계 yellow, 진행 brand-200, 현재 brand.
- 21장 활동 태그 "체험단 100명": `--orange` orange/on-brand, 높이 40, `caption-19`. 한 행에 1~2개.
- 18장 단계 배지 "CPF": `--badge` 80×58 brand-300, 현재 단계 `is-active`(brand), `body-24-eb`(700).
- 18장 하단 띠 "BEFORE": `--muted` gray-500 → `is-active` brand, `radius-sm`, 높이 69, `title-32-medium`.
- 14장 카드 모서리 탭: `.qw-tab title-32`(800) brand-tab 261×81, 모서리 0/16/0/16; `--orange`(orange-text) "실전 지원".

## 분량
알약 글자 2~8자. 배지는 영문 3자. 탭 4자.
