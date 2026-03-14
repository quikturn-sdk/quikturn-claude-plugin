---
name: logo-library
description: |
  Browse and compare available logo variants for a company from the Quikturn database.

  **Use when:**
  - User asks what logos are available for a company
  - User wants to compare logo variants (full vs icon, different sizes)
  - User needs to choose between multiple logo options
  - User asks about logo formats, dimensions, or quality

  **Not for:**
  - Directly inserting logos into presentations (use logo-insertion skill)
  - Logo design or modification
  - Non-logo image queries
---

# Logo Library Browser

## Browsing Logos

When a user wants to explore available logos for a company:

1. **Search:** `search_logos(query: "Company Name")` to find the company
2. **Get all variants:** `get_company_logos(companyId: N)` to see everything available
3. **Present options** in a clear table:

| Logo ID | Variant | Dimensions | Format |
|---------|---------|-----------|--------|
| 456 | Full wordmark | 1200x600 | png |
| 457 | Icon | 256x256 | svg |
| 458 | Full wordmark | 800x400 | jpg |

4. **Explain the differences:**
   - **Full wordmark**: The complete company logo with text. Best for title slides, headers, and company profiles.
   - **Icon**: The logo mark/symbol only, without company name text. Best for comparison grids, small spaces, and favicon-like usage.

5. **Let the user choose** before fetching. Don't automatically download all variants.

## Filtering

Users can filter by variant:
- `get_company_logos(companyId: N, variant: "full")` -- only full wordmarks
- `get_company_logos(companyId: N, variant: "icon")` -- only icons

## Format Guidance

| Format | Best For |
|--------|----------|
| PNG | General use, transparent backgrounds, presentations |
| SVG | Scalable graphics, any size without quality loss |
| JPG | Photos or logos with complex gradients (no transparency) |
| WebP | Web display (not ideal for PowerPoint) |
