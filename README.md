Maven Roasters Sales Dashboard

An Excel dashboard analysing six months of sales (January–June 2023) for Maven Roasters, a three-location coffee shop chain. Built with calculated columns, PivotTables, PivotCharts and a location slicer.

Business questions
How have sales trended over time?
Which days of the week are busiest, and why might that be?
What times of day are most popular, and does the same pattern hold across all locations?
Which products sell most and least often?
Which products drive the most revenue?
Dataset

Transaction-level sales for three locations (Astoria, Hell's Kitchen and Lower Manhattan) from January to June 2023, covering 29 product types.

Fields used: transaction_id, transaction_date, transaction_time, transaction_qty, unit_price, store_location, product_type.

Source: https://mavenanalytics.io/data-playground/coffee-shop-sales

Approach

The raw data had a quantity and unit price for each transaction, but no sales value and no weekday. I added two calculated columns to the Excel table before building anything:

Column	Formula	Why
total_sale	transaction_qty * unit_price	To measure revenue, not just count transactions
day_of_week	=TEXT([@[transaction_date]],"ddd")	To group transactions by weekday

I then built four PivotCharts and added a store_location slicer to filter the dashboard by location.

Chart	Built from	Answers
Popular Times Across All Locations	Count of transactions by hour of transaction_time, one line per store_location	Time of day, and whether it holds across locations
2023 First Half Sales	Sum of total_sale by month of transaction_date	Sales trend
Total Revenue v Total Sales Per Product	Sum of total_sale and count of transaction_id by product_type	Volume vs. revenue
Busiest Days in a Week	Count of transaction_id by day_of_week	Busiest days
Findings
Sales trend. Sales dipped from January (~81K) to February (~76K), then rose every month to ~166K in June, more than doubling from the February low. The increase held across all three locations.
Busiest days. Monday, Thursday and Friday had the most transactions, the start and end of the working week. Saturday was the quietest. The gap is small, though: roughly 21.7K transactions on the busiest day against 20.5K on Saturday, a difference of under 6%.
Time of day. Transactions peak in the morning (around 8–10 AM) at all three locations and drop sharply after 10 AM. Evenings differ by location, with Lower Manhattan tapering off earliest.
Volume vs. revenue. The best-selling product by transaction count was not the biggest revenue generator. Barista Espresso brings in the most revenue (~91K) without leading on transactions, so ranking products by volume and by revenue points to different priorities.

Figures are approximate and read from the dashboard charts.

Limitations
Six months of data. The February–June growth could be a real trend, seasonality, or both. This data can't separate them.
Small weekday differences. "Busiest day" is a mild pattern, not a strong one.
Descriptive, not causal. The dashboard shows when sales happen, not why.
Tools

Microsoft Excel: Tables, calculated columns, TEXT(), PivotTables, PivotCharts, grouping by hour and month, and slicers.

Repository contents
Maven Coffee Shop Sales.xlsx: the workbook with the data, pivot tables and dashboard
maven_roasters_dashboard.png: screenshot of the dashboard
Author

Alulutho Matoti · LinkedIn

Portfolio: https://aluluthodata.netlify.app/
