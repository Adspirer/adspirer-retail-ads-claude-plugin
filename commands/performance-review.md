---
description: Read-only scorecard for your Amazon Ads and Walmart Connect campaigns with spend, attributed sales, ACoS and ROAS, compared with the previous period, with the top problems and next actions.
argument-hint: "[platform] [period, e.g. last 7 days]"
---

# Retail performance review

Load adspirer-retail-ads-tools and adspirer-retail-ads-performance.

Use the platform and period the user gave. With none given, cover every connected platform for
the last 30 complete days, compared with the 30 days before.

1. Call get_connections_status. Work only on connected platforms and their active profile or
   advertiser. If more than one could be meant, ask which one.
2. Amazon, through amazon_ads_read: run get_amazon_campaign_performance and
   get_amazon_product_performance. When Seller Central data is connected, add
   get_amazon_combined_performance for total sales and TACoS.
3. Walmart, through walmart_ads_read: run get_walmart_ad_group_performance and
   get_walmart_ad_item_performance. Use get_walmart_out_of_budget for campaigns that capped out.
4. Show one scorecard per platform: spend, impressions, clicks, CTR, CPC, orders, attributed
   sales, ACoS, ROAS, and the change against the previous period. Keep marketplaces and currencies
   separate. Compute ratios from totals, not from averages of rows.
5. List the three findings that matter most, each with the campaign or product and the numbers
   behind it, then at most three recommended actions.
6. Say what limits the numbers: attribution windows, reporting lag, a row limit that shows only
   part of the data, or stock and buy box problems that ads cannot fix.

This command changes nothing. If the user wants to act on a recommendation, describe the exact
change, wait for their approval, and follow adspirer-retail-ads-optimization.
