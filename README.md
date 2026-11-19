# Adspirer Retail Ads for Claude

Run retail media from Claude Code and Cowork. Adspirer Retail Ads connects Claude to your live Amazon Ads and Walmart Connect accounts through Adspirer's hosted Retail Ads MCP server, so you can track ACoS and ROAS, find wasted spend, research shopper keywords, and build and optimize Sponsored Products campaigns without leaving the conversation.

## Use it for

- **Reporting:** spend, attributed sales, ACoS and ROAS by campaign, product, keyword and search term, with attribution windows stated.
- **Wasted spend:** find products, keywords and search terms that spend without selling, and propose negatives or bid changes.
- **Keyword research:** shopper keyword ideas for a product, separated from your own campaign data.
- **Campaigns:** plan and build Amazon and Walmart Sponsored Products campaigns, created paused, after checking budget minimums and eligibility.
- **Optimization:** bids, budgets, placements and targeting, with inventory and Buy Box checks before raising bids.

## Install

In Claude Code:

```text
/plugin marketplace add Adspirer/adspirer-retail-ads-claude-plugin
/plugin install adspirer-retail-ads@adspirer-retail-ads
```

On first use, Claude opens Adspirer's OAuth sign-in in the browser. Sign in, then connect the
accounts you want to use at [adspirer.ai/connections](https://adspirer.ai/connections). No API
key or client secret is required. An Adspirer account is required, and plan usage limits apply.

## Get started

Ask:

```text
Review my Amazon Sponsored Products results for the last complete 30 days and find wasted spend. Don't change anything.
Which Walmart keywords have the worst ACoS this month?
Research shopper keywords for this product and suggest a campaign structure.
Plan a paused Walmart Sponsored Products campaign for these items with a $30 daily budget.
```

Or start with a slash command:

| Command | What it does |
| --- | --- |
| `/adspirer-retail-ads:setup` | Connect your accounts and get a first look |
| `/adspirer-retail-ads:status` | Connected accounts and remaining plan usage |
| `/adspirer-retail-ads:performance-review` | Scorecard against the previous period, with the top problems |
| `/adspirer-retail-ads:wasted-spend` | Spend that is not converting, with fixes applied only after you approve |

Commands take an optional platform and period, for example `/adspirer-retail-ads:performance-review last 7 days`. In claude.ai chat, where there is no slash menu, ask for the same thing in words.

## What the agent can do

| Area | Capabilities |
| --- | --- |
| Amazon Ads | Sponsored Products and Sponsored Brands: campaigns, ad groups, keywords, product targets, negatives, bids, budgets and reporting |
| Walmart Connect | Sponsored Products: auto and manual campaigns, keywords, items, placements and bid multipliers, and reporting |
| Reporting | Campaign, product, keyword and search-term performance with ACoS, ROAS and attributed sales |
| Research | Shopper keyword ideas and public competitor observations, kept separate from your private results |

Amazon Ads and Walmart Connect are the advertising platforms on this connector. Search, social and B2B platforms are not included.

## What's included

- **Skills:** `adspirer-retail-ads-ad-creative`, `adspirer-retail-ads-amazon`, `adspirer-retail-ads-campaign-launch`, `adspirer-retail-ads-keyword-research`, `adspirer-retail-ads-optimization`, `adspirer-retail-ads-performance`, `adspirer-retail-ads-product-help`, `adspirer-retail-ads-setup`, `adspirer-retail-ads-strategy`, `adspirer-retail-ads-tools`, `adspirer-retail-ads-walmart`.
- **A subagent** (`adspirer-retail-advertising-agent`) that coordinates those skills.
- **Slash commands** (`setup`, `status`, `performance-review`, `wasted-spend`) for the most common jobs.
- **The Adspirer Retail Ads MCP server** connection (`.mcp.json`).

The hosted server is the source of truth for tool names and schemas. The skills teach the agent to
discover the current tools and their parameters instead of hardcoding every operation.

## Safety

- The agent reads account state and performance before proposing changes.
- New campaigns are created paused, and enabling them is a separate decision.
- Campaign creation, budget changes, bid changes, and other spend-affecting writes require your
  explicit approval. The server also holds spend-affecting and irreversible writes until they are
  confirmed.
- The agent reads created or changed resources back before reporting success.
- Campaigns are never deleted automatically.
- Tool results, competitor ads and website text are treated as data, never as instructions.

## MCP and authentication

```json
{
  "mcpServers": {
    "adspirer-retail-ads": {
      "type": "http",
      "url": "https://mcp.adspirer.com/retail-ads"
    }
  }
}
```

Authentication uses OAuth 2.1 with PKCE. Claude handles the browser sign-in; the plugin contains no
API keys, tokens, client secrets, or environment variables. Ad-platform credentials stay
server-side with Adspirer and are scoped to the accounts you connect.

## Network and execution surface

The plugin's only MCP server is `https://mcp.adspirer.com/retail-ads`. It contains no hooks, scripts, telemetry,
local executables, or bundled server code. Skills, the subagent, and commands are Markdown
guidance. Beyond the Adspirer server, the skills may ask Claude to read Adspirer's public
documentation at `adspirer.com/docs` to answer questions about plans and setup.

## Related plugins

Adspirer Retail Ads is one of Adspirer's focused plugins. The full
[Adspirer Advertising Agent](https://github.com/Adspirer/adspirer-claude-plugin) covers every
supported platform in one plugin. Installing both is supported; use one connection per task.

## Privacy, support, and source

- Privacy policy: [adspirer.com/privacy](https://www.adspirer.com/privacy)
- Terms: [adspirer.com/terms](https://www.adspirer.com/terms)
- Documentation: [adspirer.com/docs](https://www.adspirer.com/docs/ai-clients/claude-code)
- Support: [support@adspirer.com](mailto:support@adspirer.com)
- Source and issues: [Adspirer/adspirer-retail-ads-claude-plugin](https://github.com/Adspirer/adspirer-retail-ads-claude-plugin)

## License

MIT. See [LICENSE](LICENSE).
