---
description: Search and retrieve a company logo
argument-hint: "[company name or domain]"
---

# Logo Lookup Command

Search the Quikturn logo database and retrieve the best matching logo for a company.

## Workflow

### Step 1: Identify the Company

If a company name or domain is provided as an argument, use it directly. Otherwise ask:
- "What company logo do you need?"

### Step 2: Search for Logos

Use the `search_logos` MCP tool:
- Query with the company name, domain, or ticker
- Request up to 5 results to find the best match

### Step 3: Select the Best Logo

From the search results, select the best match using this priority:
1. **Exact domain match** (if user provided a domain)
2. **Full wordmark** variant over icon (unless user specifically asked for an icon)
3. **Highest resolution** (largest width x height)
4. **PNG format** preferred over JPG (lossless, transparent background)

If multiple companies match, present the top 3 and ask the user to confirm.

### Step 4: Fetch the Logo

Use the `get_logo` MCP tool:
- Pass the selected `logoId`
- Use `returnType: "base64"` (default) for direct insertion into slides
- If base64 fails (logo exceeds 5MB), retry with `returnType: "url"`

### Step 5: Present or Insert

- **If building a PowerPoint deck:** Insert the logo into the appropriate slide position
- **Otherwise:** Display the logo with metadata (company name, dimensions, format)
