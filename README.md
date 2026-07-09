# 🛒 Product-Price Pulse — E-Commerce Analytics (Pricing Intelligence Dashboard)

Power BI dashboard analyzing pricing, discounts, inventory, ratings, and brand performance across 1,000 products and 5 e-commerce platforms.

A Power BI dashboard that tracks pricing, discounting, stock availability, and customer engagement across five major e-commerce platforms — built to turn scattered product data into a clear pricing strategy.


📌 The Problem

If you sell (or shop for) the same type of product across multiple platforms, prices rarely line up. Discounts change constantly, stock runs out without warning, and there's no single place to compare all of it at once.

For a business, that means:


Missing chances to price competitively against other platforms
Losing sales to stockouts nobody's tracking
No easy way to know which platform is actually offering the best deal on a given product, without checking manually one by one


I wanted to see if I could pull this together into one dashboard that answers those questions instantly.


🎯 What I Built

I gathered and modeled data on 1,000+ products spread evenly across five retail platforms — Amazon, Noon, AliExpress, Jumia, and eBay (200 products each) — spanning 10 product categories including Electronics, Fashion, Beauty, Sports, and Home.

Using Power BI and DAX, I built a dashboard that tracks:


Discount penetration rate — 28.4% of products are currently discounted
In-stock availability — 83.4% of products are in stock at any given time
Average pricing across platforms and categories
Customer engagement score — a custom measure combining review volume and rating score, to surface products that are both trusted and popular
Lowest price per product — a DAX measure that automatically flags, row by row, which platform has the best price for a given product, so there's no manual comparison needed


Key DAX measures

DAXDiscounted % = 
DIVIDE(
    CALCULATE(COUNTROWS(ecommerce_dataset), ecommerce_dataset[has_discount] = TRUE()),
    COUNTROWS(ecommerce_dataset), 0
)

Min Price Per Brand = 
MINX(
    ALLSELECTED(ecommerce_dataset[retail platforms]),
    [average_price]
)

Is Min Price = 
IF([average_price] = [Min Price Per Brand], 1, 0)

The Is Min Price measure is the one I'm most proud of — it's used for conditional formatting in the matrix visual, so the platform with the lowest price for each product is automatically highlighted for the viewer, no manual sorting required.


📊 Dashboard Overview

(Add 2-3 screenshots here — e.g., the main KPI overview page, the platform comparison matrix, and the category breakdown page. Suggested captions below.)

Screenshot 1 — KPI Overview
High-level view of discount rate, in-stock rate, average price, and product volume across all five platforms at a glance.

Screenshot 2 — Platform Price Comparison
Matrix view with conditional formatting — the lowest price per product is automatically highlighted, making it easy to spot where the best deal is without manual checking.

Screenshot 3 — Category & Engagement Breakdown
Category-level view showing product volume and engagement scores, helping identify which categories are performing best across platforms.


💡 Recommendations

Based on what the data surfaced:


Standardize price monitoring across platforms. With a 28% discount rate but no centralized tracking, businesses are likely missing real-time opportunities to match or beat competitor pricing.
Watch stock availability more closely in high-engagement categories. An 83% in-stock rate still means roughly 1 in 6 products are unavailable at any time — for high-demand categories like Beauty and Sports, that's a direct hit to potential revenue.
Use engagement score, not just price, to guide promotions. Products with high ratings and review volume but no current discount are good candidates for targeted promotional pricing, since customer trust is already established.



🛠️ Tools & Tech


Power BI Desktop — dashboard development & data modelling
DAX — custom measures for KPIs, pricing logic, and conditional formatting
Power Query — data transformation and cleaning
SQL / PostgreSQL — source data querying
Python — supplementary data prep



🎥 Video Walkthrough

A narrated walkthrough of this dashboard is available on my LinkedIn: [link here]


📬 Connect

Open to Data Analyst and BI opportunities — feel free to reach out.

Prince Agyare | LinkedIn | GitHub
