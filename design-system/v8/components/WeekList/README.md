# WeekList

주차별 일정 목록. 두 꼴이 있다.

## 17장 `.qw-week`(480px, 니트 로켓 기둥 위)
- 행 높이 `week-row-h`(97, 마지막 123), 왼쪽 니트 숫자 아이콘(Icons/knit-number-1~7, 높이 65), 주차 `body-24-eb` brand + 설명 `body-20-light` gray-600(2줄까지), 오른쪽 작은 알약(`--yellow` CPF → `--tint-sm` PSF → `--solid-sm` SPF).
- 행 바탕은 `white-10`부터 10%씩 짙어져 `white-70`, 행 사이 `stroke-hairline` `line-row`. 바탕 그림은 Illustrations/rocket-column-left.png(287×1017, x=0).
- 행 7개. 설명 ≤20자/줄.

## 21장 `.qw-week--card`(흰 카드 1019×680 안)
- 머리 `.qw-week__head`: 제목 `body-24-light` 800 ink-900("주차별 스케줄") + 오른쪽 `--tint` 알약(`body-20-bold` brand "8W – 16W"); 아래 hairline `line`.
- 행 55px 간격: 주차 `body-28-eb` brand("8W", 115px 칸) + 내용 `body-28-light` ink(강조 `<b>` 700) + 오른쪽 `--orange` 알약 1~2개(`caption-19`).
- 행 9개(8W~16W). 내용 ≤16자, 알약 ≤8자.
