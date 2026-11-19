---
description: Find Amazon Ads and Walmart Connect spend that is not producing sales, such as search terms, keywords and products, and propose fixes that are applied only after you approve.
argument-hint: "[platform] [period, e.g. last 30 days]"
---

# Wasted-spend review

Load adspirer-retail-ads-tools and adspirer-retail-ads-optimization.

Use the platform and period the user gave. With none given, cover every connected platform for
the last 30 complete days.

1. Call get_connections_status. Work only on connected platforms and their active profile or
   advertiser.
2. Amazon, through amazon_ads_read: run analyze_amazon_wasted_spend for search terms with spend
   and no sales, analyze_amazon_targeting for keyword and target efficiency, and
   get_amazon_product_performance for products that spend without selling.
3. Walmart, through walmart_ads_read: there is no single waste report, so run
   get_walmart_keyword_performance and get_walmart_ad_item_performance and pick out the rows with
   spend and no attributed sales or a very high ACoS. Check get_walmart_item_alerts for items with
   stock or listing problems.
4. Separate rows with spend and no sales from rows with a high ACoS. Do not call a row wasted when
   the sample is small, when sales are still being attributed, or when the product is out of
   stock or has lost the buy box.
5. Report the top items by spend with the evidence, and the total at stake per marketplace and
   currency. For each one propose the smallest fix: a negative keyword or product target, a lower
   bid, or a pause of the narrowest resource.
6. Stop and wait. Apply only the changes the user explicitly approves, through amazon_ads_write
   or walmart_ads_write, with confirm set only after that approval. Then read the changed
   resources back and report what was applied and anything the platform rejected.

Nothing is changed until the user approves a specific change.
