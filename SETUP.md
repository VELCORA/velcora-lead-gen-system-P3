# SETUP — AI Lead Generation System (Velcora AI)

## Prerequisites

- n8n running at http://localhost:5678
- A Google account (free) for Google Sheets

---

## STEP 1: Create Your Google Sheet (Takes 30 Seconds)

1. Open your browser and go directly to: **https://sheets.new** (this instantly creates a new blank spreadsheet).
2. Rename the spreadsheet (top-left corner) to: `Lead Gen Results`
3. In **Row 1**, put these exact headers from Column A to H:
   - **A1**: `Business Name`
   - **B1**: `Website`
   - **C1**: `Email`
   - **D1**: `Phone`
   - **E1**: `Address`
   - **F1**: `Industry`
   - **G1**: `Source URL`
   - **H1**: `Discovered At`

---

## STEP 2: Copy Your Google Sheet ID

1. Look at your browser's URL bar while on that spreadsheet. The URL looks like this:
   `https://docs.google.com/spreadsheets/d/1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgvE2upms/edit#gid=0`
2. Copy the long random string between `/d/` and `/edit` (e.g., `1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgvE2upms`). **That is your Sheet ID.**

---

## STEP 3: Connect It in n8n

1. Go to your n8n tab: **http://localhost:5678**
2. Click on workflow: **AI Lead Generation System - Velcora AI**
3. Double-click the last node: **Save emails to Google Sheet**
4. In the **Document ID** field, paste the Sheet ID you copied in Step 2.
5. Click **Save** in the top right.

---

## STEP 4: Run and Test

1. Click **Execute Workflow** (top right or bottom of the trigger node).
2. When prompted for input data in the manual trigger, enter:
   ```json
   [{"query": "cafes in Mumbai"}]
   ```
3. Click **Execute Node** or **Test workflow**.
4. Check your `Lead Gen Results` Google Sheet — emails will appear automatically!

---

## Workflow Details

- **Workflow ID in n8n:** `X4bpwfPoyiRY6fL5`
- **GitHub Repo:** [VELCORA/velcora-lead-gen-system](https://github.com/VELCORA/velcora-lead-gen-system)
- **Cost:** $0 (Uses only core n8n nodes, zero paid APIs)
