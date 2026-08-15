# Velcora Lead Engine

Automatically scrapes business emails from Google Maps based on a list of queries. Pure n8n core nodes, zero paid APIs.

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
| Workflow name | Velcora Lead Engine |
| Nodes | 26 (core nodes only) |
| Cost | $0 — no paid APIs |
| Status | Active in n8n (localhost:5678) |

> ⚠️ The setup guide and Fiverr gig template reference older iterations of this engine. The `workflow.json` in this repo is the current, full Velcora Lead Engine.

## Files

- `workflow.json` — importable n8n workflow
- `SETUP.md` — step-by-step setup guide
- `FIVERR-GIG.md` — service listing template for delivering this engine

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
