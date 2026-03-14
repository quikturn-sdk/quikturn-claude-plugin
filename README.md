# Quikturn Logo Plugin for Claude

Search and insert company logos into pitch decks, CIMs, teasers, and financial presentations — powered by the [Quikturn](https://getquikturn.io) logo database.

Built for [Claude Cowork](https://claude.com/product/cowork), also compatible with [Claude Code](https://claude.com/product/claude-code).

## What It Does

Connects Claude to Quikturn's database of thousands of company logos via [MCP](https://modelcontextprotocol.io). When Claude is building or populating a presentation, it can automatically search for, select, and insert the right logo — no manual downloading, resizing, or formatting.

**Three MCP tools:**

| Tool | Purpose |
|------|---------|
| `search_logos` | Search by company name, domain, or ticker. Returns metadata (no image data). |
| `get_logo` | Fetch a specific logo as base64 image data or a signed URL. |
| `get_company_logos` | List all logo variants (full wordmark, icon) for a company. |

## Getting Started

### Cowork

Install from [claude.com/plugins](https://claude.com/plugins/) — search for "Quikturn".

When you first use a Quikturn tool, Claude will prompt you to authenticate via your Quikturn account.

### Claude Code

```bash
claude plugin install quikturn-sdk/quikturn-claude-plugin
```

## Commands

| Command | Description |
|---------|-------------|
| `/logo [company]` | Search and retrieve the best matching logo for a company |
| `/logos [company]` | Browse all available logo variants and choose one |

### Examples

```
/logo Apple
/logo goldmansachs.com
/logos Microsoft
```

## Skills

Skills activate automatically when relevant — you don't need to invoke them.

| Skill | When It Activates |
|-------|-------------------|
| **logo-insertion** | Building or populating PowerPoint slides that need company logos |
| **logo-library** | Browsing available logos, comparing variants, or choosing between options |

### Logo Insertion

When Claude is building a deck, the `logo-insertion` skill teaches it to:

- Use full wordmarks on title slides, icons for comparison grids and strip profiles
- Size logos consistently across multi-company slides (comps tables, buyer lists)
- Prefer PNG (transparent background) over JPG
- Fall back to signed URL mode for logos over 5MB
- Never stretch or distort — always maintain aspect ratio

### Logo Library

When you ask about available logos, the `logo-library` skill teaches Claude to:

- Show all variants with dimensions and format info
- Explain the difference between full wordmarks and icons
- Let you choose before downloading

## Supported Slide Types

| Slide Type | Logo Variant | Typical Size |
|-----------|-------------|-------------|
| Title / cover | Full wordmark | 300-500px width |
| Company profile | Full wordmark | 200-300px width |
| Comps table | Icon | 40-60px |
| Strip profile | Icon | 40-50px |
| Buyer list | Icon | 40-60px |
| Market landscape | Icon | 30-50px |
| Deal tombstone | Full wordmark | 150-250px |

## Authentication

This plugin connects to Quikturn's MCP server at `logos.getquikturn.io/mcp`. Authentication is handled via OAuth — when you first use the plugin, you'll be prompted to sign in with your Quikturn account.

A Quikturn account on the **Launch** plan or higher is required for MCP access.

## Requirements

- A [Quikturn](https://getquikturn.io) account (Launch plan or higher)
- Claude Cowork or Claude Code

## Links

- [Quikturn](https://getquikturn.io) — company logo platform
- [MCP Documentation](https://modelcontextprotocol.io) — Model Context Protocol specification
- [Claude Plugins](https://claude.com/plugins/) — browse and install plugins

## License

[Apache License 2.0](./LICENSE)
