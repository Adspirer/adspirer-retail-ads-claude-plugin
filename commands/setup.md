---
description: Connect Amazon Ads and Walmart Connect to Adspirer, choose the profiles and advertisers to work on, and get a first look at what is running.
---

# Set up Adspirer Retail Ads

Load adspirer-retail-ads-tools and adspirer-retail-ads-setup.

1. Call get_connections_status. If it fails because the connector is not signed in, tell the user
   to connect the Adspirer Retail Ads connector (in Claude Code: run /mcp, choose
   adspirer-retail-ads and sign in), then stop and wait. Never ask for a password or token in chat.
2. List what is connected. Use list_amazon_profiles through amazon_ads_read and
   list_walmart_advertisers through walmart_ads_read to name each profile or advertiser with its
   marketplace and currency. Name the active one on each platform.
3. If a platform the user wants is missing, give them https://adspirer.ai/connections and wait.
   Walmart Connect can need partner access and an advertiser id rather than a sign-in. If several
   profiles exist and it is unclear which to use, ask. Activating or switching accounts changes
   the active set, so call activate_ad_accounts only after the user confirms the exact accounts.
4. Take a first look at the last 30 days on each connected platform:
   get_amazon_campaign_performance through amazon_ads_read for Amazon, and
   get_walmart_ad_group_performance through walmart_ads_read for Walmart. Skip a platform that is
   not connected; do not invent numbers for it.
5. Finish with a short summary: what is connected, what is not, spend, attributed sales, ACoS and
   ROAS for each platform, and what to try next: /adspirer-retail-ads:performance-review for a
   full scorecard or /adspirer-retail-ads:wasted-spend to find spend that is not converting.

This command changes no campaign and creates no files. Build a brand workspace only if the user
asks for one.
