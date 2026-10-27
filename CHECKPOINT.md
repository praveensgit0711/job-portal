# Checkpoint: Canada Job Portal

Keep this file with the project. To resume in any new chat, upload `index.html` and this file and say:
"Resume the Canada Job Portal from CHECKPOINT.md. Continue with the next stage only. Free tiers only."

## Status

| Stage | Description | State |
|---|---|---|
| 1 | UI shell: profile, 10 saved searches (add/rename/delete), filters, dashboard, tracker, CSV export, JSON backup, match estimate, LinkedIn and Job Bank search links | Delivered. Syntax-checked only, not yet browser-tested by the owner |
| 2 | Free Cloudflare Worker proxy plus 1-2 verified sources (candidates: Adzuna, Jooble, Job Bank open data) | Not started |
| 3 | Test with real API responses, check Apply links, tune matching | Not started |
| 4 (optional) | Scheduled Worker + free email for alerts | Not started, not promised |

## Decisions

- Free tiers only. No paid hosting, APIs or databases.
- No scraping of LinkedIn. LinkedIn appears only as search links, never as listings.
- No sample or invented jobs. The results area stays empty until a real source responds.
- API keys live only as Worker secrets, never in index.html.
- All user data (profile, searches, tracker) is in browser localStorage. Use Settings > Export backup regularly.
- Match scores are keyword estimates and labelled so. Career-break friendliness is shown only when the posting text says so.

## Proxy contract (what Stage 2 must provide)

`GET {workerUrl}/jobs?q=<comma keywords>&l=<location>` returns JSON:

```json
{
  "jobs": [{
    "id": "source's own id", "source": "Adzuna", "title": "", "company": "",
    "location": "", "workMode": "Remote|Hybrid|On-site|null",
    "type": "Full-time|Part-time|Contract|Temporary|Internship|Casual|null",
    "level": "Entry-level|Junior|Intermediate|Senior|null",
    "salaryMin": null, "salaryMax": null, "salaryText": "",
    "posted": "ISO date", "description": "", "url": "", "applyUrl": ""
  }],
  "sources": [{"name": "Adzuna", "ok": true, "count": 20, "error": null}]
}
```

The Worker must send `Access-Control-Allow-Origin` for your site, and map failures into `sources[].ok=false` with a readable `error`.

## Known limits

- Live retrieval does not work until Stage 2.
- Refresh and auto-refresh run only while the page is open. No background monitoring or email alerts exist.
- Browser notifications work only while the page is open.
- localStorage is per browser and per device.

## Next action

Stage 2: confirm each source's current free-tier terms, rate limits and attribution rules, then build the Worker.
