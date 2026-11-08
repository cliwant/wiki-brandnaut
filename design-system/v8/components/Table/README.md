# Table

표 세 꼴과 왼쪽 사이드 패널(27·28·29장).

## `.qw-table`(27장 예산표, 1040px)
- 머리행 `brand-bright` 바탕 높이 `row-head-h`(78), `body-24-bold` on-brand 왼정렬. 본문 행 `row-h`(60), 셀 좌우 `card-pad-xs`(24), 행 사이 `stroke-hairline` `line-table`.
- 첫 칸 `body-20-medium` ink-900, 산출 근거 칸 `body-15`(2줄), 금액 `is-num` 오른정렬, 나머지 `body-20-light`. 합계 행 `is-total`은 `brand-050` 바탕.
- 행 11개 + 합계(27장). 셀 줄바꿈 2줄까지.

## `--blue`(29장 협력 주체 표)
- 머리행 brand 높이 62, 본문 행 92, 구분선 `line-soft`, 글자 `body-18`(첫 칸 brand 500). 행 4개, 셀 2줄 ≤20자.

## `--rounded`(28장 조직표, 960px)
- 머리행 brand 높이 52, 위 모서리 `radius-lg`, 글자 `body-20-medium` on-brand. 행 53, 구분선 `line-softer`, 아래 모서리 둥글게. 강조 런 `.qw-hl` 700("사업경력 13년"). 행 4개.

## `.qw-panel`(27·29장 왼쪽 590px)
- 흰 둥근 패널(덱은 그림자 있는 그림 — 여기선 hairline `line-table` 테두리), 안쪽 64/61. `.qw-panel__bar` 8×50 brand 세로 바 + 제목 `panel-title`(32px, 행간 40) ink-900. 항목: 번호 `body-24-bold` `brand-deep`("01 사전 확인") + 본문 `body-20-light` gray-700 2줄. 항목 4개.
- 장 구성: 왼쪽 헤드라인(`headline` 2줄, 강조 런) + 리드 `body-24-bold` 300 굵기 gray-700(27장은 1800 L) + 패널, 오른쪽 1186px `surface-panel`(`.qw-side`) 위에 패널 제목(`.qw-panel-head panel-title`) + 표.
