# Canada Job Portal (Stage 1)

## Run it now (free)
1. Put `index.html` in a folder and double-click it. It runs in any modern browser with no install.
2. Or host it free: create a GitHub repository, upload `index.html`, then Settings > Pages > deploy from the main branch.

## What works today
- Editable profile and 10 editable saved searches (add, rename, delete, save).
- All filters, dashboard, job details, match estimate, save and track jobs, notes, CSV export, JSON backup and restore.
- "LinkedIn Jobs search" and "Job Bank search" links built from your current filters. These open the sites' own search pages. They are not imported listings.

## What does not work yet
- Live job listings. They need the Stage 2 proxy, so the results area is empty by design. No sample jobs are shown.
- Background monitoring and email alerts. Not implemented.

## Your data
Stored only in this browser. Use Settings & data > Export backup regularly.

## API keys
Never put keys in `index.html`. In Stage 2 they will be stored as secrets in a free Cloudflare Worker, and you will paste only the Worker's URL into Settings.

See `CHECKPOINT.md` for status and how to resume.
