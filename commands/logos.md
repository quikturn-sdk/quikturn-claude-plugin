---
description: Browse all logo variants for a company
argument-hint: "[company name or domain]"
---

# Browse Company Logos Command

Show all available logo variants for a company so the user can choose.

## Workflow

### Step 1: Identify the Company

If a company name or domain is provided as an argument, use it directly. Otherwise ask:
- "What company's logos would you like to browse?"

### Step 2: Search for the Company

Use the `search_logos` MCP tool to find the company:
- Query with the provided name or domain
- If multiple companies match, ask the user to confirm which one

### Step 3: Get All Variants

Use the `get_company_logos` MCP tool with the confirmed `companyId`:
- Do not filter by variant -- show all available options

### Step 4: Present Options

Display a table of all available logos:

| # | Variant | Dimensions | Format |
|---|---------|-----------|--------|
| 1 | Full wordmark | 1200x600 | png |
| 2 | Icon | 256x256 | svg |
| 3 | Full wordmark | 800x400 | jpg |

Ask: "Which logo would you like to use? (Enter the number)"

### Step 5: Fetch Selected Logo

Use the `get_logo` MCP tool with the selected `logoId`:
- Use `returnType: "base64"` by default
- If base64 fails (>5MB), retry with `returnType: "url"`
