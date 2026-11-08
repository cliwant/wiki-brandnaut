# Timeline

레일과 점. 가로 레일(10·11장)과 세로 네온 선(8장) 두 가지.

## 가로 `.qw-timeline`
- 구간마다 `rail-h`(8px) 레일: 비활성 `brand-200`, 현재 `is-active` brand(10장 가운데). 11장 `--full`은 네 구간 모두 brand.
- 점 `dot`(24): 흰 채움 + `stroke-regular` brand 테두리, 활성은 brand 채움. 레일 왼끝에 놓는다.
- 글자(점에서 30px 들여): 키커 `kicker-20` brand("모집 4일 전") → 제목 `tag-30-medium` ink → 설명 `body-24-light` gray-600. 11장은 제목 `title-32` brand("프로그램 개요")만 두고 아래 `.qw-dash` 목록.
- 구간 3~4개, 제목 ≤12자, 설명 1줄 ≤22자.

## 세로 `.qw-neon`(8장, 검정 장)
- 왼쪽에 `stroke-regular` brand 세로선(장 전체 높이, 사진 패널과 목록 패널의 경계 x=1091). 항목마다 `dot-neon`(20px) brand 점이 선 위에, 간격 110.
- 항목: 번호 `headline` 300 굵기 brand("01") → 니트 원형 아이콘 `icon-3d`(99) → 제목 `headline` on-brand(≤6자). 항목 4개. 아래 `.qw-neon__note headline` 300 굵기 3줄(≤14자).
