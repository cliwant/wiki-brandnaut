# PhotoBeforeAfter

전면 사진 위에 BEFORE(왼쪽)와 AFTER(오른쪽)를 맞세우고, 가운데 니트 화살표와 라벨, 반투명 칩으로 프로그램이 주는 것을 적는 장(9·13·20·22장).

## 부품
- `.qw-ba--left` / `.qw-ba--right`: 라벨 `label-spaced`(자간 4px) + 본문 `title-48-photo`(2줄 ≤12자). 기본 y=787, `--high`(9장)는 y=648. 폭 826.
- `.qw-ba__arrow`: Icons/arrow-knit-small.png 357×240, 중앙(x 783). `.qw-ba__center title-36-eb`: 화살표 위 라벨(13장 "1만원 챌린지").
- `.qw-chip`: `scrim-55` 바탕, 높이 `chip-h`(106), `radius-chip`(21), 가운데 정렬. 첫 줄 `title-36`(≤22자), 둘째 줄 `overlay-25`(brand-100, ≤40자; `<b>`는 orange-light "운영사:"). 장당 2개(위 y≈228/322, 아래 y≈691/705).
- `.qw-steps`(9장): white-65 선 + 17px 점 4개, 마지막 점 `is-active`(brand). 라벨 `body-24-medium` ≤12자.
- `.qw-ba__caption label-26`(20·22장): 오른쪽 아래 한 줄 요약, 500 굵기.

## 배치 규칙
- 사진은 BEFORE/AFTER가 좌우로 나뉘어 읽히는 것(13장 왼쪽 군중 → 오른쪽 팀). 흰 글자엔 `shadow-text-50/55`.
- 라벨·번호는 SlideHeader 사진 변형. 헤드라인은 9장처럼 둘 수도(`headline-photo`), 13·20장처럼 생략할 수도 있다.

## 소비자가 주는 것
사진, BEFORE/AFTER 문구, 중앙 라벨, 칩 2개(제목·부제), 선택: 단계 4개 / 하단 캡션.
