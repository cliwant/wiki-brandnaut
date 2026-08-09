# 브랜드넛 덱 렌더 누적 규칙 (design-system 버전 무관)

> **용도**: 브랜드넛 제안서 렌더(S6) 시작 시, 이 파일의 [general] 규칙을 해당 프로젝트의
> `render_feedback.json`에 시드하여 모든 fit 서브에이전트가 `{FEEDBACK_GUIDANCE}`로 받게 한다.
> 디자인 시스템을 새 템플릿에서 재추출(v4, v5…)해도 이 파일은 남는다 — **버전 파일이 아니라
> 고객 레벨 규칙이 누적처다.** 새 보완이 확정될 때마다 여기 추가할 것.
>
> 이력: KNU-대구앵커-경진대회 세션(2026-08-01) 피드백 8건 + 청소년 기업가정신재단 세션
> (2026-08-08) 지적 5건 통합. 원문은 각 프로젝트 `render_feedback.json` 참고.

## [general] 항상 적용

1. **표지**: 원문 표지의 이미지·전체 레이아웃을 그대로 유지한 채 내용만 교체한다. cover intent의
   **allowed variant 전부를 합성**해야 원문이 된다(v3 기준: fullbleed-background-pattern +
   hero-circular-photo + cover-title-block + cover-submission-footer). 플랜에 1개 variant만 있으면
   나머지를 보충하고, 빈 슬롯은 프로젝트 메타(발주처명·"주식회사 브랜드넛"·제안 일자)로 채운다.
   이미지 슬롯은 <p:pic> placeholder 보존.
2. **목차**: 템플릿 TOC 원본 슬라이드의 **헤더(상단 타이틀 영역) 포함** 전체 구성을 그대로 따른다
   (임의 간소화 금지).
3. **간지(장 표지)**: 각 章(level-1 단원) 시작마다 section_divider 슬라이드를 넣는다.
   S5 플랜에 없으면 렌더 단계에서 보충한다(cover_toc가 간지를 안 만드는 파이프라인 공백).
   간지는 로마자 패널만이 아니라 **핵심 메시지 + 하위 목차를 합성**한 원문 구성으로
   (v3 기준: section-numeral-title-panel + key-message-with-numbered-list).
4. **푸터**: 좌측 발주처(로고 또는 발주처명), 중앙 페이지넘버, 우측 "주식회사 브랜드넛".
   frame 레이아웃(FooterCustomer/PageNumber/FooterBidder)이 소유 — fit이 푸터 furniture를 만들거나 지우지 않는다.
   ※ FooterCustomer 텍스트는 프로젝트마다 발주처명으로 갱신 (v3는 2026-08-08 청소년 기업가정신재단으로 설정됨).
5. **헤더 통일**: 모든 본문 슬라이드의 브레드크럼+페이지 타이틀 서식·위치를 덱 전체 동일하게.
6. **레이아웃 반복 완화**: 인접 슬라이드와 같은 variant·같은 구성이 반복되면 배치(전폭/2컬럼/카드/스텝)와
   밀도를 바꿔 시각적 단조로움을 깬다. 원본 팔레트·폰트는 유지.
7. **내부 전략 언어 금지**: 정성평가·배점·승부처·기술점수 등 심사 구조 언급 일체 금지.
   같은 주장은 발주처 관점 언어로 전환.
8. **무관 이미지 금지**: 콘텐츠와 무관한 템플릿 사진을 채우지 않는다. 관련 이미지가 없으면
   빈 placeholder(연회색 박스 + 📷 필요 사진 설명)로 미완임이 보이게 한다.
9. **이미지 슬라이드 구성**: 이미지를 쓰는 슬라이드는 한쪽 절반에 큰 이미지 1~2장 + 반대쪽에
   텍스트/도식. 작은 사진 카드 나열 금지.
10. **텍스트만 있는 슬라이드 금지**: 리드 스테이트먼트류 문장 2개만 나열하는 구성은 안 된다.
    콘텐츠에 유형·항목·단계가 있으면 카드그리드/타임라인/스텝플로우/비교표 등 도식형 variant로
    표현한다(해당 intent의 allowed_variant_ids 중 카드·플로우·테이블 계열 활용).
11. **폰트 크기 하한 (v3 캔버스 보정).** v3 캔버스는 18,288,000 × 10,287,000 EMU(20인치 폭)로
    표준 16:9(13.3인치)의 **1.5배**다. 원본 컴포넌트의 명목 폰트 크기를 그대로 쓰면 화면에서
    1/1.5로 작아 보인다. 따라서 본문 10pt 미만, 제목 16pt 미만은 쓰지 말고, 원본이 그보다 작으면
    **1.2~1.5배 상향**해 조판한다(본문 12pt·제목 20pt 내외 권장). 카드 수를 줄이거나 문장을 압축해
    폰트를 키울 공간을 만들 것 — 폰트를 줄여 내용을 우겨넣는 것은 금지.
12. **다른 입찰/프로젝트 언급 금지**: 위키 근거([coNN] 등) 인용 시 그 근거가 **이 제안서와 무관한
    다른 진행 중 입찰**(예: 경쟁 중인 타 사업)을 가리키지 않는지 반드시 확인한다. "제출할 수
    있습니다", "원하시면 보여드리겠습니다" 같은 애매한 어조 대신, 실제 완료된 자사 실적만
    확정형 어조로 서술한다("~습니다", 조건부·판매 멘트 금지).

## [확인 후 적용] 템플릿 종속 규칙 (대림대 v1/v2에서 확정, 새 템플릿 적용 여부는 유저 확인)

- **타이틀 하단 원라이너 콜아웃 밴드**: 페이지 타이틀 바로 아래 그 슬라이드 핵심 메시지 1문장을
  담은 전폭 콜아웃. 본문 폰트 12.5pt, 기본 진회색, 핵심 구절 1~3곳만 파란색 볼드(문장 전체 파란색 금지).
- **표지 배경 이미지**: 표지 전면 배경 그림(맨 뒤) + 타이틀 가독성 유지.

## v3 카탈로그 보강 이력

- **2026-08-09: frame 헤더·푸터 폰트 상향.** `frame/ppt/slideLayouts/slideLayout2.xml`의
  SectionBreadcrumb 9→13pt, PageNumber·FooterBidder·FooterCustomer 9→10.5pt. 20인치 캔버스에서
  9pt는 실효 6pt로 읽기 어려웠다. frame 수정은 catalog.json SHA와 무관하므로 재패키징만 하면
  전 슬라이드에 일괄 반영된다(개별 슬라이드 refit 불필요). 백업: `slideLayout2.xml.bak-fontfix`.
- **2026-08-08: `single-bordered-bullet-box`(FALLBACK_VARIANT_ID) 신규 정의.** v3 원본 추출본에
  이 fallback variant가 아예 없었음(S5 완료 시점부터 알려진 결함 — floor 슬라이드가 빈 슬롯으로
  렌더될 위험). `accent-bar-note-panel` 톤을 재사용해 최소 정의(단일 richtext 슬롯 `items`)를
  추가. 이게 없으면 `intent_id: null`인 floor 슬라이드(요구사항 fallback 등)가 본문 없이
  렌더된다 — **카탈로그를 처음 준비할 때 반드시 이 variant가 있는지 확인할 것.**

- **2026-08-08: `text-with-supporting-media` 이식.** v3(배재대 추출본)에는 이미지 슬롯을 가진 body
  variant가 하나도 없었다(표지의 hero-circular-photo 제외). v1(대림대)에서 이식해
  `program_structure_overview`·`recruitment_and_selection` intent의 allowed_variant_ids에 추가.
  실제 컨셉/레퍼런스 사진이 없는 프로젝트에서는 `primary_image` 슬롯을 연회색 placeholder
  (📷 필요 사진 설명)로 채운다. **카탈로그를 고칠 때마다 해당 프로젝트의
  `slide_plan.json._meta.catalog_sha256`도 같이 갱신할 것** — 안 하면 S6 Stage 0 gate가
  mismatch로 막는다.
- 새 컨셉/레퍼런스 이미지가 필요한 섹션(사업 구성안·기획전략·홍보전략 등 Ⅲ장 위주)이 또
  나오면, 다른 필요 이미지 variant(`side-feature-image`·`banded-feature-blocks` 등, 전부 v1에
  있음)도 같은 방식으로 이식 검토.

## 운영 메모

- wiki-hub `.gitignore`가 `customers/`를 통째로 무시한다 → design-system·이 파일 모두 **git으로
  공유되지 않는다.** 다른 머신·클론(wiki-brandnut-경북대, kim-yesol의 wiki-brandnaut)과 수동 동기화
  필요. gitignore 정책 변경은 위키 관리자 결정 사항.
- 버전 계보: v1(대림대 추출) → v2(v1+헤더 보완, wiki-brandnut-경북대에 있음) → v3(배재대 재추출,
  v2 보완 미승계 — 이 사고가 이 파일을 만든 이유).
