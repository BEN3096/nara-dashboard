# 나라장터 대시보드 고정 규칙

Locked at: 2026-06-02 KST
Owner: Jobdori
Process: Nara procurement v4 only
Public URL: https://ben3096.github.io/nara-dashboard/
Repository: `/Users/dori/nara-dashboard`

## 고정된 범위

현재 대시보드는 디자인과 전체 정보 구조를 고정한다. 사용자가 명시적으로 재디자인을 요청하지 않는 한 `index.html`의 레이아웃, 색상 체계, 상호작용, 요약 표시 구조를 변경하지 않는다.

고정 항목:

- Soft Civic 톤: 밝은 회녹색 배경, 흰색 패널, 차분한 teal/navy 강조색.
- 상단 헤더, 상태 pill, 6개 KPI 카드, 필터 도구막대, 좌측 공고 목록, 우측 상세 패널 구조.
- 공고별 원문 탭과 첨부 요약 탭 흐름.
- `첨부 요약` 본문은 아래 5개 섹션으로 고정한다.
- 첨부파일 원문 미리보기는 요약 하단에서 파일별로 접고 펼칠 수 있게 유지한다.
- 줄바꿈이 없는 원문 블록은 사람이 읽기 좋은 문단 단위로 정리해 표시한다.

## 수정 가능한 범위

일반 업데이트에서는 아래 데이터 파일만 교체하거나 수정한다.

- `nara_dashboard_v4.json`
- `nara_attachment_summaries_v4.json`

수정 가능 항목:

- 공고 목록, 마감일, 금액, 기관명, 지역, 판정 상태.
- KPI 수치와 첨부 처리 통계.
- 첨부 전체 요약과 파일별 요약.
- 원문 미리보기 텍스트의 줄바꿈/가독성 보정.

## 첨부 요약 고정 템플릿

모든 공고의 첨부 요약은 같은 틀을 사용한다.

```json
{
  "sections": [
    {"title": "사업 개요", "items": []},
    {"title": "과업 범위", "items": []},
    {"title": "참가 자격", "items": []},
    {"title": "제출·평가", "items": []},
    {"title": "주의할 점", "items": []}
  ]
}
```

작성 규칙:

- 각 섹션은 2-4개 문장형 bullet로 정리한다.
- 원문에 없는 내용을 추정해서 확정 표현으로 쓰지 않는다.
- 교수법인 수행 가능성, 공동수급, 지역 제한, 실적 제한, 제안서 제출 방식은 보이면 반드시 포함한다.
- 단순 파일명 나열보다 실제 과업 내용과 제한 조건을 먼저 보여준다.

## 금지

- 사용자 요청 없이 `index.html`의 디자인, 레이아웃, 색상, 탭 구조를 변경하지 않는다.
- v4 이전 수집본이나 구버전 스크립트를 현재 표준 입력으로 사용하지 않는다.
- API 키, 토큰, 인증 정보는 repo와 옵시디언 메모에 기록하지 않는다.
- 첨부 요약 틀을 공고별로 임의 변경하지 않는다.
- 첨부 원문을 줄바꿈 없는 긴 문자열로 그대로 노출하지 않는다.

## 배포 전 확인

1. `node -e "JSON.parse(require('fs').readFileSync('nara_dashboard_v4.json','utf8')); JSON.parse(require('fs').readFileSync('nara_attachment_summaries_v4.json','utf8'))"`
2. `python3 -m http.server 8000`
3. `http://localhost:8000`에서 공고 목록, 상세 패널, `첨부 요약` 버튼을 확인한다.
4. git diff에서 `index.html`이 의도 없이 바뀌지 않았는지 확인한다.
