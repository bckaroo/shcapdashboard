# SHCAP Dashboard — Sleepy Hollow Climate Action Tracker

A lightweight, embeddable dashboard for tracking progress on the Sleepy Hollow Climate Action Plan.

## Architecture

```
Google Sheets (village residents edit)
        ↓ published as CSV
HTML Dashboard (reads live data)
        ↓ iframe embed
ESRI StoryMap (public-facing)
```

## Files

| File | Purpose |
|------|---------|
| `index.html` | The dashboard — single file, no dependencies |
| `shcap-data.json` | Embedded fallback data (49 actions from the CAP) |
| `shcap-template.csv` | Google Sheets import template |

## Setup: Google Sheets Integration

### 1. Create a new Google Sheet
- Go to Google Sheets → New spreadsheet
- Import `shcap-template.csv` (File → Import → Upload)
- Or manually create columns matching the CSV headers

### 2. Publish to Web
- In the Sheet: **File → Share → Publish to web**
- Select: **Sheet1** + **CSV** format
- Click **Publish**
- Copy the generated URL

### 3. Configure the Dashboard
- Open `index.html` in a text editor
- Find: `const GOOGLE_SHEET_CSV_URL = '';`
- Paste your URL: `const GOOGLE_SHEET_CSV_URL = 'https://docs.google.com/spreadsheets/d/e/YOUR_ID/pub?output=csv';`

### 4. Deploy
Upload `index.html` + `shcap-data.json` to any static host:
- **GitHub Pages** (free) — easiest
- **Netlify** (free) — drag & drop
- **Vercel** (free)

### 5. Embed in StoryMap
- In the StoryMap builder, add an **Embed** block
- Paste your hosted dashboard URL
- Set height to ~800px or enable scrolling

## Column Reference

| Column | Description | Example Values |
|--------|-------------|----------------|
| ID | Unique action identifier | CE-01, CF-1.2a, RT-3.3b |
| Category | Top-level grouping | Clean Energy & Water Systems, Coastal Flooding |
| Strategy | Sub-grouping within category | Renewable and Clean Energy Systems |
| Action | Name of the action | Integrate Clean Energy Systems... |
| Description | Full description text | (from CAP) |
| Type | Mitigation or Adaptation | Mitigation, Adaptation |
| Priority | Priority level | Priority, Standard |
| CSC Points | Climate Smart Communities points | 20-40 |
| Status | Current status | Not Started, In Progress, Complete |
| % Complete | Numeric progress 0-100 | 0, 25, 50, 75, 100 |
| Target Date | Completion target | 2027, 2030 |
| Responsible Party | Who's responsible | Village Board, DPW |
| Funding | Funding sources | NYSERDA, Federal ITC |
| Implementation Projects | Related projects | Sponge Village Stormwater Master Plan |
| Notes | Free-form notes | Feasibility study underway |

## Data Model

The 49 actions are organized into:

### Mitigation (12 actions)
- **Net Zero Mobility** (4) — VMT reduction, building design, infrastructure, lighting
- **Clean Energy & Water Systems** (3) — Clean energy, CCA, forestry
- **Climate Positive Communities** (3) — Circular waste, local food, green business
- **Enabling Measures** (2) — Progress reports, Climate Coordinator

### Adaptation (37 actions)
- **Coastal Flooding** (16) — Stormwater, nature-based solutions, public health, water supply, river reconnection
- **Inland Flooding** (10) — Sponge Village, stormwater, green infrastructure, resident engagement
- **Rising Temperatures** (11) — Cool corridors, forestry, food systems, Pocantico River

## Dashboard Features

- ✅ Overall progress bar with category breakdowns
- ✅ Filter by type (Mitigation/Adaptation), status, and category
- ✅ Collapsible category sections
- ✅ Priority actions highlighted (★)
- ✅ Responsive — works on mobile
- ✅ No dependencies — single HTML file
- ✅ Google Sheets CSV integration (live data)
- ✅ Embedded JSON fallback (works offline)
