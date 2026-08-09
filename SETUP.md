# SETUP — AI Lead Generation System (Velcora AI)

## Prerequisites

- n8n running at http://localhost:5678
- A Google account (free) for Google Sheets

## Step 1: Import the Workflow (done — re-import only if needed)

Workflow is already imported and ACTIVE in n8n:
- ID: `X4bpwfPoyiRY6fL5`

To re-import (fresh copy):
```bash
python -c "import json, urllib.request; wf=json.load(open(r'C:\Users\sithe\Documents\Default Project\velcora-portfolio-projects\lead-gen-system\workflow.json', encoding='utf-8')); req=urllib.request.Request('http://localhost:5678/api/v1/workflows', data=json.dumps(wf).encode(), headers={'Content-Type':'application/json','X-N8N-API-KEY':'<API_KEY>'}, method='POST'); print(json.loads(urllib.request.urlopen(req).read().decode())['id'])"
```

## Step 2: Create the Google Sheet (REQUIRED — one-time)

1. Go to https://sheets.new
2. Create a spreadsheet named `Lead Gen Results`
3. First row headers:

| A | B | C | D | E | F | G | H |
|---|---|---|---|---|---|---|---|
| Business Name | Website | Email | Phone | Address | Industry | Source URL | Discovered At |

4. Copy the **sheet ID** from the URL: `https://docs.google.com/spreadsheets/d/<SHEET_ID>/edit`

## Step 3: Point the Workflow at the Sheet (REQUIRED)

1. Open n8n → **AI Lead Generation System - Velcora AI**
2. Open the **Save emails to Google Sheet** node
3. Credential: **Google Sheets account** (already linked)
4. Document: paste your `<SHEET_ID>` from Step 2
5. Sheet: leave as `gid=0` (first tab)
6. Save

## Step 4: Add Your Queries

In the **Run workflow** manual trigger, when executing, enter queries as a JSON array:
```json
[{"query": "digital marketing agencies in Mumbai"}, {"query": "real estate agents in Delhi"}, {"query": "restaurants in Bangalore"}]
```
Format: `<business type> in <location>`

## Step 5: Test

1. Click **Execute workflow**
2. Watch **All executions** (scraper runs in background per query)
3. Check `Lead Gen Results` sheet for emails
4. If no emails: some businesses simply don't publish emails — try different queries, or loosen the email regex in the **Filter irrelevant emails** node

## Node Map

| Node | Role |
|------|------|
| Run workflow | Manual trigger — paste your queries |
| Loop over queries | One scraper run per query |
| Search Google Maps with query | HTTP request to Google Maps search |
| Scrape URLs from results | Code — extracts listing URLs |
| Filter irrelevant URLs | Regex filter |
| Loop over URLs / pages | Pagination + per-listing fetch |
| Scrape emails from page | Code — regex email extraction |
| Save emails to Google Sheet | Google Sheets append |

## Troubleshooting

- **Google Sheets auth error**: re-auth the credential (Settings → Credentials → Google Sheets account)
- **Too slow**: lower the wait node delay or remove it (Sticky Note 2)
- **Emails missing**: regex too strict in **Filter irrelevant emails** — adjust it
