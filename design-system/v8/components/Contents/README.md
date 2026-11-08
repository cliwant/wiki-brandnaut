# Contents

목차 장(2장). 왼쪽에 'Contents' 키커와 2줄 제목, 오른쪽에 로마 숫자 장 목록과 소항목·쪽번호.

## 배치 규칙
- 키커 `.qw-toc__kicker title-32-medium`(brand) x=90 y=88. 제목 `.qw-toc__title display-80-bold`(ink) y=146, 폭 528, 2줄 ≤7자.
- 목록 `.qw-toc__list` x=700부터: 장 행은 로마 숫자(`body-28-bold` brand, 50px 칸) + 장 이름(`body-28-bold` ink-900), 높이 40.
- 소항목 `.qw-toc__sub body-20-light`(gray-700): 들여쓰기 64, 높이 28, 쪽번호는 오른끝 67px 칸에 오른정렬. 장 사이 간격 14.
- 분량: 장 8개 × 소항목 1~3개까지(2장 실측 8장·18항목, y 88→632). 더 많으면 소항목을 줄인다.
- 장 이름은 대표 표기 그대로("Chapter 0. 1만원 챌린지"). 페이지 번호는 Contents 다음 장부터 센다.

## 소비자가 주는 것
제목 2줄, 장 목록 [{numeral, name, items:[{title, page}]}].
