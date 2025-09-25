# 📊 DAX Measures – Sales Dashboard

This file documents all the DAX measures used in the Sales Dashboard project.

Total Sales = SUM(Sales[Amount])
Total Profit = SUM(Sales[Profit])
Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0)
Total Quantity = SUM(Sales[Quantity])
Total Orders = DISTINCTCOUNT(Sales[Order ID])
Distinct Customers = DISTINCTCOUNT(Sales[CustomerName])
AOV = DIVIDE([Total Sales], [Total Orders], 0)
YTD Sales = TOTALYTD([Total Sales], 'Date'[Date])
YoY Sales Growth % =
VAR ThisYear = [Total Sales]
VAR LastYear = CALCULATE([Total Sales], SAMEPERIODLASTYEAR('Date'[Date]))
RETURN DIVIDE(ThisYear - LastYear, LastYear, 0)
Sales Rank = RANKX(ALL(Sales[Sub-Category]), [Total Sales], , DESC)
TopN Products Sales = IF([Sales Rank] <= SELECTEDVALUE('TopN'[Value]), [Total Sales])
Sales per Customer = DIVIDE([Total Sales], [Distinct Customers], 0)
Profit per Order = DIVIDE([Total Profit], [Total Orders], 0)