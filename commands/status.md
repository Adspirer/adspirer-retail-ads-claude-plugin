---
description: Show which Amazon Ads profiles and Walmart Connect advertisers are connected and active on Adspirer Retail Ads, and how much of your plan's usage is left.
---

# Connection and usage status

Load adspirer-retail-ads-tools.

1. Call get_connections_status. Show a table: platform | profile or advertiser name and id |
   marketplace | active or not | connection health.
2. Call get_usage_status. Show tool calls used, the limit, the plan name and the reset date.
3. Point out anything that needs attention: an expired or failing connection, a platform that is
   not connected, no active account on a platform, or usage close to the limit.

If the connector is not signed in, tell the user to connect Adspirer Retail Ads (in Claude Code:
run /mcp, choose adspirer-retail-ads and sign in) and stop.

This command only reads. To connect a platform, send the user to
https://adspirer.ai/connections. Switch or activate accounts only when the user asks and confirms
the exact accounts. Never buy, upgrade or renew a plan: if usage has run out, say so, link
https://www.adspirer.com/pricing and wait.
