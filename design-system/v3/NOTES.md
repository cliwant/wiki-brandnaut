# 브랜드넛 design-system v3

기준 원본: **`2026.7.31_배재대학교_로컬크리에이터 양성_제안서.pptx`** 추출본.
v1·v2(대림대 청하 제안서 계열)와는 **다른 원본에서 뽑은 별개 계열**이다. 슬라이드 캔버스도 다르다
(v1·v2 = 12192000×6858000, **v3 = 18288000×10287000**).

경북대 KNU-대구앵커 경진대회 제안서(36p)를 v3로 처음 끝까지 만들면서 확인된 결함을 고쳐 반영했다.

## 추출 직후 상태의 결함과 조치

### 1. frame이 사실상 비어 있었다 → 본문 레이아웃 신규 저작
추출본의 `frame/`은 master·layout에 도형이 하나도 없었다(레이아웃 680바이트). 그래서 카탈로그가
선언한 헤더 placeholder(`ph idx 20/21`)가 상속받을 geometry가 없어 **모든 본문 슬라이드의 상단이 백지**로
렌더됐다. 원본 덱 4쪽에서 좌표·서식을 실측해 본문 레이아웃(`slideLayout2.xml`)을 새로 만들었다.

| 요소 | 좌표 (EMU) | 서식 |
|---|---|---|
| 상단 바(다크) | 0,0 / 18288000×38405 | `0F172A` |
| 상단 바(블루 세그먼트) | 0,0 / 3810305×38405 | `2563EB` |
| 브레드크럼 `ph body idx=20` | 1143000,533095 / 7620610×191110 | 9pt b spc135 `64748B` |
| 페이지 타이틀 `ph body idx=21` | 1143000,857707 / 16002000×495605 | 28pt b spc-75 `0F172A` |
| 타이틀 언더라인 | 1143000,1524305 / 571500×28346 | `2563EB` |

### 2. layout id가 물리 파일과 매핑되지 않았다
패키저는 `layout-N` → `slideLayoutN.xml` 규칙으로 매핑하는데 추출본 id가 `layout-body`/`layout-bare`라
**전부 slideLayout1로 fallback**됐다. `layout-1`(표지·간지용 여백) / `layout-2`(본문)로 개명하고
master의 `sldLayoutIdLst`·rels·`[Content_Types].xml`에 layout2를 등록했다.

### 3. 푸터가 없었다 → 좌·중·우 3분할 푸터 추가
`slideLayout2`에 중앙 페이지 번호(`a:fld type="slidenum"`)와 우측 제안사명(고정 `주식회사 브랜드넛`)을
정적 도형으로, 좌측 발주처명은 master의 `dt` placeholder(idx 10)로 넣었다. 발주처명은 프로젝트마다
`master_fills`의 `date` 슬롯으로 채운다.
> `ftr`/`sldNum` placeholder를 슬라이드에 주입하는 방식은 LibreOffice가 렌더에서 숨겨버려 쓸 수 없었다.
> `dt`만 정상 렌더된다.

### 4. content_box가 슬라이드 전폭이었다
`layout-2`의 content_box가 `x=0 / w=18288000`이라 본문이 가장자리까지 붙었다. 원본 여백 기준
**x=1143000 / y=1700000 / w=16002000 / h=8000000**으로 고쳤다. `layout-1`은 전면 유지.

### 5. 표지가 제목 없이 나왔다
`cover` intent의 `allowed_variant_ids`가 알파벳순이라 `cover-submission-footer`(제출처·제안사·제출일만
있고 제목 슬롯 없음)가 첫 후보로 잡혔다. `cover-title-block`이 먼저 오도록 순서를 바꿨다.
표지는 **4종 합성**이다 — `fullbleed-background-pattern` + `hero-circular-photo` + `cover-title-block`
+ `cover-submission-footer`.

### 6. 목차가 통째로 생략됐다
`cover_toc.py`는 intent id **`table-of-contents`** 를 찾는데 추출본은 `toc`였다. 개명하고
`allowed_variant_ids`를 `toc-section-summary-card-grid` 하나로 좁혔다(리스트형 variant가 먼저 잡히면
목차가 아닌 문장 컴포넌트가 선택된다).

### 7. intent별 컴포넌트 후보가 2~4개뿐이라 슬라이드가 평탄화됐다
추출본은 원본 덱에서 그 intent에 **실제로 쓰인** variant만 허용했다. 그 결과 같은 intent로 분류된
연속 슬라이드가 똑같은 화면이 됐다. 표지·목차·간지·클로징 전용을 뺀 **공용 본문 컴포넌트 35종**을
모든 본문 intent에 열었고, 원본 덱이 그 intent에서 실제로 쓴 것은 **`signature_variant_ids`** 에 따로 남겼다.
> 후보가 넓어진 대신 intent만으로는 형태가 갈리지 않는다. 연속 슬라이드가 같은 조합으로 수렴하지
> 않도록, 설계 단계에서 **직전 슬라이드가 쓴 조합을 입력으로 주는 것**이 사실상 필수다.

### 8. `meta.style_conventions` 신설
헤더/푸터 담당 구분, 키 메시지 한 줄 + 구분선, 좌우 여백, 카드 밀도(블록 2~3개·항목 3~5개),
그룹 헤더 밴드 사용, 내부 입찰 전략 언어(정성평가·배점·평가항목) 금지를 규약으로 명시했다.

## 남은 한계 (다음 개정 후보)

- **목차 카드가 4칸 고정**이다. 장이 5개 이상인 제안서는 5번째 카드를 핏 단계에서 저작해야 한다
  (경북대 건은 3+2 그리드로 만들었다). 6칸 리사이즈 가능한 목차 variant가 있으면 좋다.
- **표지 원형 사진이 원본 덱의 스톡 이미지**다. 사업에 맞는 사진으로 교체하는 절차가 필요하다.
- adornment는 **`title` 슬롯을 가진 것만** 써야 한다. `layout_fills.py`가 블록 헤딩을 항상 `title`로
  내보내서, `band_label`·`kicker`만 가진 adornment를 고르면 슬롯명 불일치로 슬라이드가 강등된다.
- `vertical-funnel-stat-flow`의 stat은 큰 숫자 run에 단위가 들어가고 숫자가 비는 조립 버그가 있었다.
  이 variant를 쓸 때 렌더 결과의 숫자를 확인할 것.

## 검증

경북대 제안서 36페이지(표지·목차·간지 5·본문 28·클로징) 전량 렌더로 확인했다.
`verify_deck` 12/12 통과, floor 0건, fallback 0건.
