# Supply-Chain-Revenue-and-Fulfilment-Analytics
Supply Chain Revenue and Fulfilment Analytics using POWER BI

**Objective:** This project analyses supply chain operations data to deliver actionable insights into inventory management, supplier performance, logistics efficiency, and order fulfilment. The dashboards are designed around key performance indicators (KPIs) and allow dynamic filtering by region, product category, supplier, and time to support data-driven decision-making.

**File Name:** Supply_Chain_DashBoard.pbix

**Tools Used:**
- Power BI
- Power Query
- DAX
- Microsoft Excel
- Dashboards

**Data Overview:** The dataset comprises comprehensive logistics and commercial records, including:
- *Financial Metrics:* Total Revenue (82.69M), Total Profit (30.87M), Gross Profit % (37.34%), and Average Profit (3.86K).
- *Fulfillment & Volume:* Total Units Sold (36K), Average Delivery Days (20.67), and Delay Delivery % (0.94).
- *Operational Segments:* Warehouse Codes (e.g., WARE-PUJ1005, WARE-NBV1002), Sales Channels (In-Store, Online, Distributor, Wholesale), and Sales Team performance.
- *Temporal Data:* Monthly order counts and revenue trends from 2018 to 2020.

**Key KPIs and Why They Matter:**
- *Total Revenue (82.69M):* Serves as the primary indicator of the supply chain's commercial scale and market demand.
- *Gross Profit % (37.34%):* Measures the overall financial efficiency of the operations, indicating how much of every dollar earned is retained as profit.
- *Average Delivery Days (20.67):* A vital logistics metric that tracks the speed of the supply chain from order to fulfillment.
- *Delay Delivery % (0.94):* Monitors fulfillment reliability; keeping this number low is essential for maintaining customer satisfaction and operational standards.
- *Total Units Sold (36K):* Tracks the volume of physical goods moving through the warehouse network, critical for capacity planning.

**Key DAX Formulae Used:**
- *Total Revenue* = SUM(main[Revenue])
- *Total_Units* = SUM(main[Order Quantity])
- *Gross_margin%* = DIVIDE([Total_Profit], [Total_Revenue])
- *Inventory_Status* = SWITCH(TRUE(),  Inventory[Stock] <= 100, "Low Stock",  Inventory[Stock] <= 500, "Medium Stock",  Inventory[Stock] > 500, "High Stock")
- *Delivery_Time* = DATEDIFF(Orders[Order_Date], Orders[Delivery_Date], DAY)
- *Delay Delivery(over 7 days)* = CALCULATE([OrderLine], FILTER(main, main[Delivery Days]>7))
- *On_Time_Delivery* = DIVIDE( CALCULATE(COUNT(Orders[Order_ID]), Orders[Delivery_Status] = "On Time"), COUNT(Orders[Order_ID]))
- *Inventory_Turnover* = DIVIDE(SUM(Sales[Cost_of_Goods_Sold]), AVERAGE(Inventory[Stock_Value]))
- *Total_Cost* = SupplyChain[Transportation_Cost] + SupplyChain[Inventory_Cost] + SupplyChain[Warehouse_Cost]

**Key Insights from the Dashboard:**
- *Warehouse Performance:* WARE-NBV1002 is the most active hub, accounting for 31.57% (26.11M) of order value. Despite differences in volume, Gross Margins remain remarkably consistent across all warehouses, ranging from 36.84% to 37.81%.
- *Channel Efficiency:* In-Store sales are the dominant revenue driver, contributing 34.04M (41.16%) of total revenue. In contrast, the Wholesale channel represents the smallest segment at 9.21M (11.14%).
- *Order Seasonality:* Monthly orders show a significant increase in the latter half of the year, peaking in July (795 orders) and August (791 orders), as well as December (791 orders).
- *Logistics Consistency:* The average delivery time is stable across different warehouses, hovering around 20 to 21 days, indicating a standardized fulfillment process across the network.
- *Sales Team Productivity:* There is a clear correlation between revenue and profit across teams, with Team 26 emerging as a top performer with profits exceeding 1.3M.

**Conclusion:** The Supply Chain Management dashboard provides a high-level view of both commercial health and operational speed.
- It enables administrators to identify top-performing warehouses and channels, allowing for targeted resource allocation toward high-volume areas like "In-Store" sales.
- It supports logistics optimization by highlighting delivery benchmarks and tracking the percentage of delayed deliveries to ensure fulfillment standards are met.
- By monitoring Gross Profit % alongside revenue trends, the dashboard assists in maintaining healthy margins even as the volume of units sold fluctuates throughout the year.
