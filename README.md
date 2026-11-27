# SERPHub MCP Server

[![SERPHub MCP connector – tool definition quality and endpoint health on Glama](https://glama.ai/mcp/connectors/io.serphub/serphub/badges/score.svg)](https://glama.ai/mcp/connectors/io.serphub/serphub)

Connect AI assistants (Claude Desktop, Cursor, VS Code, Windsurf, Antigravity, and any MCP-compatible client) directly to your **[SERPHub](https://serphub.io)** SEO data — covering Google Search Console, Bing Webmaster Tools, Yandex Webmaster, technical site audits, local rank grids, AI visibility (AEO), backlinks, and client reports.

- **MCP Endpoint:** `https://serphub.io/mcp`
- **API & MCP Documentation:** [https://serphub.io/api-docs](https://serphub.io/api-docs)
- **Protocol:** Model Context Protocol (Streamable HTTP) with OAuth 2.0 or Sanctum Bearer token authentication

---

## Quick Start

### 1. Get your SERPHub token (or use OAuth)
1. Sign in to [SERPHub](https://serphub.io/login) (free tier available).
2. Open **Account → MCP & API** (`https://serphub.io/account/mcp`) to create a personal access token, or connect directly via OAuth when your client supports MCP OAuth discovery.

### 2. Add to your AI client

#### Cursor / VS Code / Antigravity (`.mcp.json` or `mcp.json`)
```json
{
  "mcpServers": {
    "serphub": {
      "url": "https://serphub.io/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_SERPHUB_TOKEN"
      }
    }
  }
}
```

#### Claude Desktop (`claude_desktop_config.json`)
Claude Desktop supports remote MCP servers via `mcp-remote` (or native Connectors):
```json
{
  "mcpServers": {
    "serphub": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://serphub.io/mcp",
        "--header",
        "Authorization: Bearer YOUR_SERPHUB_TOKEN"
      ]
    }
  }
}
```

---

## Available MCP Tools (37 Tools)

### Sites & Audits
- `list_sites` — List websites in your SERPHub account (call this first to get `site_id`)
- `get_site` — Get site details, health score, and connection status
- `create_site` — Add a new website to your account
- `run_audit` — Start a full technical SEO crawl/audit
- `get_audit_progress` — Poll progress of an active audit
- `get_audit` — Retrieve completed audit summary and scores
- `get_issues` — List technical SEO issues filtered by severity or type
- `get_pages` — Inspect crawled pages, status codes, titles, meta, and word counts
- `get_internal_links` — Analyze internal link graph and orphan pages
- `get_no_index` — List pages blocked from indexing (`noindex`, `robots.txt`, canonicals)
- `get_site_snapshots` — Compare historical site audit snapshots
- `get_uptime` — Check uptime monitoring status and incidents

### Search Console, Bing & Yandex Intelligence
- `get_search_overview` — Combined clicks, impressions, CTR, and average position across connected search engines
- `get_keywords` — Top queries with clicks, impressions, CTR, and position
- `get_visibility` — Search visibility score and trend
- `get_cannibalization` — Detect keywords where multiple URLs compete for rankings
- `get_content_decay` — Identify pages losing clicks/impressions over time
- `get_clusters` — Topic/keyword clusters
- `get_search_intent` — Query intent classification

### AI Visibility (AEO / GEO)
- `get_aeo_status` — AI readiness and visibility overview
- `run_aeo_audit` — Run an AI Engine Optimization audit
- `run_geo_check` — Check brand/citation presence across AI answer engines
- `get_ai_mentions` — Track brand mentions in AI responses
- `get_prompt_bank` — Manage tracked AI prompts

### Local SEO & Google Business Profile
- `get_local_rank_scan` — Local Pack / rank grid scan results
- `get_gbp_search_terms` — Google Business Profile discovery search terms
- `get_gbp_reviews` — Customer reviews and ratings

### Backlinks, Competitors, Content & Workflows
- `get_backlinks` — Backlink profile and referring domains
- `get_competitors` — Tracked competitor domains
- `get_reports` — Generated white-label SEO reports
- `list_content_briefs` / `create_content_brief` — SEO content briefs
- `list_tasks` / `create_task` / `update_task` — SEO action tasks
- `get_notifications` / `mark_notifications_read` — Account alerts

---

## Example Prompts

- *"Call `list_sites` and summarize the top high-severity technical SEO issues across my sites."*
- *"Find keyword cannibalization on site ID 23 and list which URLs should be merged or canonicalized."*
- *"Check content decay over the last 90 days and suggest which pages to refresh first."*
- *"Compare our Google Search Console and Bing performance for the last 30 days."*

---

## Links

- Website: [https://serphub.io](https://serphub.io)
- API & MCP Docs: [https://serphub.io/api-docs](https://serphub.io/api-docs)
- White-Label SEO Reports: [https://serphub.io/features/white-label-seo-reports](https://serphub.io/features/white-label-seo-reports)

## License

MIT — see [LICENSE](./LICENSE).
