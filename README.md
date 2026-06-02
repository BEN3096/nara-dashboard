# nara-dashboard

나라장터 도시재생 사업 용역 대시보드입니다.

Public URL: https://ben3096.github.io/nara-dashboard/

## Current Status

- Design lock: 2026-06-02
- Owner handoff: Jobdori
- Process: Nara procurement v4 only
- Local preview: `python3 -m http.server 8000`

## Locked Dashboard Surface

The dashboard design, layout, and interaction model are frozen. Future work should update content and data only unless the user explicitly asks for a redesign.

Locked files and behavior:

- `index.html`: Soft Civic visual design, responsive layout, filters, bid list, detail panel, and attachment-summary interaction.
- Attachment summary layout: fixed sections for `사업 개요`, `과업 범위`, `참가 자격`, `제출·평가`, `주의할 점`.
- Document preview layout: attachment files remain expandable below the summary and must preserve readable line breaks.

See `DASHBOARD_LOCK.md` for the full lock rules.

## Mutable Data Surface

Use these files for normal content updates:

- `nara_dashboard_v4.json`: dashboard metadata, KPI values, bid rows, and attachment status.
- `nara_attachment_summaries_v4.json`: fixed-template attachment summaries and document previews.

Do not put API keys or private credentials in this repository.

## Update Checklist

1. Regenerate v4 data from the Jobdori v4 process.
2. Replace only the JSON files listed above.
3. Validate JSON parsing.
4. Preview locally and check the `첨부 요약` tab.
5. Commit and push only intended dashboard/data changes.
