# 브랜드넛 design-system v2 — 변경 요약

기준: v1(대림대 청하 제안서 추출본) + **KNU 대구앵커 경진대회 런(`~/.contrl/runs/knu-anchor/2026-08-01_r1`)에서 유저가 확정한 스타일**을 시스템 기본값으로 반영.

## 변경 사항

### 1. 표지(cover-title-block) 갱신
- 전면(full-bleed) 배경 이미지 `<p:pic>` 추가 — `DSMEDIA::775f08b876c84075.png` (media/에 신규 등재, = 런 `assets/cover_bg_A.png`, sha1[:16] content-address).
- 타이틀: 흰색(#FFFFFF) sz4000 볼드, Gmarket Sans Medium, 단일 문단(긴 제목은 wrap).
- 서브라인(tagline): 밝은 회청색 #C9D8E4 sz1800.
- 슬롯: `cover_title`(shape 21) + `cover_tagline`(shape 6). v1의 eyebrow(`cover_subtitle`) 도형은 확정 표지에 없어 제거.
- preview.png = 런 slides/01/after.png.

### 2. 목차 variant 신규: `table-of-contents-list`
- v1에서 목차가 생략된 원인: cover_toc.py는 intent id **`table-of-contents`** 에 저작된 variant를 찾는데, v1 intent id는 `toc`였고 저작 variant도 리스트형이 아니었음.
- v2: intent `toc` → **`table-of-contents`** 로 개명, `allowed_variant_ids: ["table-of-contents-list"]`, layout_affinity **layout-1**(전면 콘텐츠 박스 — 목차가 자체 타이틀을 그림).
- 슬롯 스키마 (cover_toc.py `_repeated_toc_slot` 계약과 일치):
  - `chapters` — kind `repeated`, `cardinality {resizable:true, min:3, max:8, base:5}`
    - `toc_section_marker` (로마숫자 마커, #005F7A 볼드) — cover_toc가 I·II·III…로 자동 충전
    - `toc_section_title` (장 제목, #1F2933 볼드) — RFP section_tree level-1 제목으로 자동 충전
    - `toc_section_summary` (회색 하위 소제목 요약 줄) — **cover_toc는 채우지 않음**(미충전 시 자동 blank), S5/핏 에이전트 몫
    - `toc_pages` (시작 페이지 번호, #005F7A 볼드) — flatten.json이 주어지면 자동 해석
  - `subtitle` — 목차 타이틀 아래 제안서 전체 제목 한 줄 (cover_toc 미충전 → blank)
- 점선 리더(·········)·헤어라인·'목 차' 타이틀·포인트 바는 **정적 도형**(슬롯 밖 → blank_unfilled가 건드리지 않음).
- 기존 `numbered-contents-grid`는 카탈로그에 보존하되 목차 기본에서 제외(used_by_intents 비움).
- preview.png = 런 slides/02/after.png.

### 3. layout-3 헤더 보완
- layout-4의 헤더 furniture/placeholder를 layout-3에 이식: `section_breadcrumb`(y=457200) + `page_title`(y=749808), ph idx 20/21.
- `frame/ppt/slideLayouts/slideLayout3.xml`에 동일 placeholder sp 추가.
- content_box를 layout-4/5와 동일하게 y=1500000, h=4800000으로 조정 — 본문 원자가 헤더 아래로 배치되도록(헤더 불일치 원인 제거).

### 4. 스타일 컨벤션 (catalog description + meta.style_conventions에 명시)
1. **원라이너 콜아웃 밴드**: 모든 본문 슬라이드는 페이지 타이틀 바로 아래 콜아웃 밴드 1개 — 05 규격: `E8F2F7` roundRect + `0089B8` 좌측 세로 바, 본문 sz1250, 기본 색 `#1F2933`, 핵심 구절 1~3곳만 `#0089B8` 볼드. **문장 전체 파란색 금지.**
2. **이미지 스플릿 구성**: 이미지 사용 시 한쪽 절반에 큰 이미지 1~2장 + 반대쪽 설명. 소형 사진 카드 나열 지양.
3. **사진 슬롯 배제 금지**: 사진 확보 전이면 `{description, convention:"photo"}` placeholder로 저작하고 description에 "필요 사진 설명"을 기입.
4. **헤더 통일 규격**: 브레드크럼 11pt `#6B7785`(y=457200) / 페이지 타이틀 20pt 볼드 `#1F2933`(y=749808).

## 검증 (2026-08-02)
- `loaders.load_catalog` 정상 (variants 39, intents 31).
- `cover_toc.py --catalog v2 --rfp KNU rfp.json --input-slides flatten.json` → **cover=True, toc=True**, 5개 장 행 + 페이지 번호(3/8/13/19/29) 자동 해석.
- `assemble_slide.py --front-matter` → 표지(배경 이미지+흰 타이틀)·목차(마커/제목/점선/페이지) 시드 렌더 확인.

## 알려진 제약
- cover_toc의 `_strip_enumerator`는 ASCII 로마숫자만 제거 — RFP 장 제목이 유니코드 `Ⅲ.`(U+2162 등) 접두를 쓰면 마커와 제목에 번호가 중복 표기됨(예: "III  Ⅲ. 사업 수행 계획"). 핏 에이전트가 정리하거나 rfp.json 제목을 ASCII로 정규화 필요.
- 장 수 < base(5)면 미사용 행의 텍스트는 자동 blank되지만 점선 리더·헤어라인(정적 도형)은 남음 — 핏 에이전트 정리 몫. 장 수 > 5면 초과분이 마지막 행에 병합됨(`_merge_rows`).
- 표지 `cover_title`은 단일 문단 주입 — 런에서처럼 3줄 수동 분할된 형태는 핏 단계에서 조정.

## 추가 컨벤션 (2026-08-01 KNU 런 후반 확정)
- **내부 전략 언어 금지** — 슬라이드 텍스트에 정성평가·배점·승부처·평가항목 우위 등 심사 구조 언급 절대 금지. 발주처 관점 언어로 전환해 쓸 것.
- **무관 이미지 금지·빈 슬롯 처리** — 콘텐츠와 무관한 템플릿 사진을 채우지 말고, 관련 이미지가 없으면 빈 placeholder(연회색 박스 + 📷 필요 사진 설명)로 남겨 교체 대상임을 명시할 것.
