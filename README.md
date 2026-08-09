# AI Lead Generation System - Velcora AI

Automatically scrapes business emails from Google Maps based on a list of queries. Built from the proven n8n template (206K views, 0 paid APIs — only n8n core nodes).

## What It Does

1. You provide search queries (e.g. `cafes in Mumbai`)
2. Searches Google Maps for matching businesses
3. Extracts business listing URLs
4. Fetches each listing's HTML
5. Extracts emails using regex (no third-party APIs)
6. Saves all emails to a Google Sheet

## Facts

| Item | Value |
|------|-------|
| Template source | https://n8n.io/workflows/2567 (MIT, 206,002 views) |
| n8n workflow ID | `hwiZNuABczj2Cd4y` |
| Workflow name | AI Lead Generation System - Velcora AI |
| Nodes | 26 (core nodes only) |
| Cost | $0 — no paid APIs |
| Status | Active in n8n (localhost:5678) |

## Files

- `workflow.json` — importable workflow (rebranded for Velcora AI)
- `template-2567-raw.json` — untouched original template API response
- `SETUP.md` — step-by-step setup guide
- `FIVERR-GIG.md` — Fiverr gig listing template

## How to Use

1. Open the workflow in n8n
2. Click "Execute workflow" (manual trigger) and enter a JSON array of queries like:
   ```json
   [{"query": "digital marketing agencies in Mumbai"}]
   ```
3. Emails land in the configured Google Sheet

> The workflow runs the scraper as a background execution per query (Execute Workflow node targets `$workflow.id`). Watch the "All executions" tab.

---
© Velcora AI — anonymous freelance AI automation agency.
