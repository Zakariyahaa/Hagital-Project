# **Project Background** 

Hagital Store is a regional retailer operating across the United States, offering a wide range of products across Technology, Furniture, and Office Supplies categories. This project presents a detailed analysis of Hagital’s sales performance between 2014 and 2017, with a focus on revenue growth, product profitability, regional dynamics, shipping efficiency, and customer behavior.

Hagital had accumulated a substantial volume of sales data over four years, but much of it had yet to be fully explored for strategic insights. This project combines Power BI visualizations, SQL analysis, and DAX-driven metrics to uncover trends and opportunities that can drive commercial growth and operational improvements.

Insights and recommendations are provided on the following key areas:

* **Sales Trends Analysis**: Review of year-over-year sales, average order value (AOV), and seasonal fluctuations.
* **Product-Level Performance**: Profitability analysis by product category and sub-category, with a focus on margin optimization.
* **Regional Insights**: Evaluation of sales and profit distribution across the West, East, Central, and South regions.
* **Customer & Team Analysis**: Identification of top-performing customers, discount behavior, and sales team contributions.
* **Operational Efficiency**: Assessment of shipping timelines and their effect on profit margins.

An interactive Power BI dashboard is available for download [here](https://github.com/Zakariyahaa/Hagital-Sales-Record-Analysis/blob/main/Sales%20Overview.png).

The SQL queries used to answer business questions and validate results can be downloaded [here](https://github.com/Zakariyahaa/Hagital-Sales-Record-Analysis/blob/main/hagital_sales_analysis_queries.sql).

The full cleaned dataset used for analysis can be accessed [here](https://github.com/Zakariyahaa/Hagital-Sales-Record-Analysis/blob/main/All%20Sales%20Records_PBI_sql.xlsx).

The PowerPoint presentation file with details of Key Findings, Recommendations & Limitations can be downloaded [here](https://github.com/Zakariyahaa/Hagital-Sales-Record-Analysis/blob/main/Hagital_Store_Sales_Insights_Presentation.pptx).

--- 

# **Data Structure & Initial Checks**

The dataset used in this project is a consolidated file titled **`All Sales Records_PBI.xlsx`**, which merges historical order records from 2014 to 2017. The unified **Sales Table** contains **9,994 transactions** across **23 columns**, covering everything from order details to customer demographics and profitability metrics.

The original source data includes:

* `2014 Sales Records.xlsx`
* `2015 Sales Records.xlsx`
* `2016 Sales Records.xlsx`
* `2017 Sales Records.xlsx`
* Combined and cleaned into: [`All Sales Records_PBI.xlsx`](https://github.com/Zakariyahaa/Hagital-Sales-Record-Analysis/blob/main/All%20Sales%20Records_PBI_sql.xlsx)

A summary of the structure is shown below:

| Column Name        | Data Type | Description                                              |
| ------------------ | --------- | -------------------------------------------------------- |
| Order ID           | Text      | Unique order identifier                                  |
| Order Date         | Date      | Date when order was placed                               |
| Ship Date          | Date      | Date when the order was shipped                          |
| Ship Mode          | Text      | Mode of shipment (e.g., Standard Class, Same Day)        |
| Customer ID        | Text      | Unique customer identifier                               |
| Customer Name      | Text      | Full name of the customer                                |
| Segment            | Text      | Customer segment: Consumer, Corporate, or Home Office    |
| Sales Rep          | Text      | Name of the salesperson handling the order               |
| Sales Team         | Text      | Sales team the rep belongs to                            |
| Sales Team Manager | Text      | Team manager overseeing the sales rep                    |
| City               | Text      | Customer's city                                          |
| State              | Text      | Customer's state                                         |
| Postal Code        | Text      | ZIP or postal code                                       |
| Region             | Text      | Regional grouping (West, East, Central, South)           |
| Product ID         | Text      | Unique product identifier                                |
| Category           | Text      | Product category: Technology, Furniture, Office Supplies |
| Sub-Category       | Text      | Specific product line within the category                |
| Product Name       | Text      | Description of the product                               |
| Sales              | Decimal   | Total sales value                                        |
| Quantity           | Integer   | Number of units sold                                     |
| Discount           | Decimal   | Discount applied (as a decimal value)                    |
| Profit             | Decimal   | Net profit from the transaction                          |

**Data Cleaning & Preparation Process**:

* All files were loaded and appended using Power Query.
* Duplicates, nulls, and text inconsistencies were resolved.
* Data types were validated and corrected (dates, numbers, text).
* A derived **date hierarchy** (Year, Quarter, Month, Day) was added.
* Columns such as `Location ID` were removed due to redundancy.
* Calculated measures using DAX were created for actual revenue, average revenue, and margin analysis.

> The final dataset was validated and optimized for Power BI visualizations and SQL querying.

---

# **Executive Summary**

## **Overview of Findings**

The analysis of Hagital Store’s sales records (2014–2017) reveals strong growth in revenue and profitability, though uneven across regions, product categories, and customer segments. While Technology and Office Supplies deliver high returns, Furniture is consistently underperforming due to low margins and high shipping delays. Additionally, a small proportion of customers and products generate the majority of revenue, posing both concentration risks and upsell opportunities.

Power BI dashboards visualize all trends, and SQL queries support deeper interrogation of customer, sales, and regional dynamics. The findings outlined below form the basis for strategic recommendations designed to enhance Hagital’s commercial performance.

The entire interactive dashboard can be downloaded [here](https://github.com/Zakariyahaa/Hagital-Sales-Record-Analysis/blob/main/Sales%20Overview.png).

![Sales Overview](https://github.com/user-attachments/assets/8fcdb48a-0bf3-4e5e-bcb5-24b4b4f07eb4)

---

## **Sales Trends**

| Metric                    | 2014         | 2015         | 2016         | 2017         |
| ------------------------- | ------------ | ------------ | ------------ | ------------ |
| Total Revenue             | \$484,247.50 | \$470,532.51 | \$609,205.60 | \$733,215.26 |
| Total Profit              | \$49,543.97  | \$61,618.60  | \$81,795.17  | \$93,439.27  |
| Unique Orders             | 969          | 1,038        | 1,315        | 1,687        |
| Average Profit Margin (%) | 10.2%        | 13.1%        | 13.4%        | 12.7%        |

* **Strong Growth Trajectory:** Hagital Store’s revenue increased from \$484K in 2014 to \$733K in 2017 (+51%), while profit grew even faster (+89%), reflecting improving margins.
* **Regional Leaders:** The West and East regions account for nearly 62% of total sales and 68% of profit, driven largely by California and New York.
* **Product Profitability Imbalance:** Technology and Office Supplies deliver healthy margins (\~17%) and represent 68% of profit, whereas Furniture generates 32% of revenue but only 6% of profit (2.5% margin).
* **Customer Concentration Risk:** The top 20% of customers contribute \~48% of revenue, with a few high-volume buyers (e.g., Sean Miller) operating at a loss due to excessive discounts.
* **Operational Insights:** Faster shipping (≤3 days) correlates with higher margins (14.2% vs. 12.5%), highlighting the profit impact of logistics efficiency.
* **Seasonal Opportunity:** Sales peak consistently in October–November, suggesting that targeted pre-holiday promotions can further amplify revenue.

---

## **Product Performance**

### **By Category**

| Category        | Revenue      | Profit       | Profit Margin (%) |
| --------------- | ------------ | ------------ | ----------------- |
| Technology      | \$836,154.03 | \$145,454.95 | 17.4%             |
| Office Supplies | \$719,047.03 | \$122,490.80 | 17.0%             |
| Furniture       | \$741,999.80 | \$18,451.27  | 2.5%              |

* **Technology** delivers the highest revenue and margins.
* **Furniture**, despite high sales, is underperforming profit-wise in dicating potential over-discounting or costly logistics. 
  
  ![Product OrderbyState Region](https://github.com/user-attachments/assets/646be559-c3d1-4e2a-ba7e-2cf319a13583)

### **Top Sub-Categories (by Revenue)**

| Sub-Category | Revenue      | Profit           | Margin |
| ------------ | ------------ | ---------------- | ------ |
| Phones       | \$330,007.10 | \$44,516.25      | 13.5%  |
| Chairs       | \$328,449.13 | \$26,590.15      | 8.1%   |
| Binders      | \$203,412.77 | \$30,221.64      | 14.8%  |
| Tables       | \$206,965.68 | **–\$17,725.59** | –8.6%  |

> Sub-categories like **Tables** and **Bookcases** generate revenue but often at a loss. Conversely, **Phones** and **Binders** have strong ROI.

![Historical Rev  by Region](https://github.com/user-attachments/assets/410fe28b-0be9-4588-9afa-f39527d4cda5)

---

## **Recommendations**

### Reevaluate Furniture Strategy

* Audit pricing and shipping costs—Tables and Bookcases frequently sell at a loss.
* Introduce minimum margin thresholds for promotions in low-performing sub-categories.
* Improve delivery speed or offer freight surcharge options for bulky items.

### Prioritize High-ROI Product Lines

* Expand marketing and bundling around Phones, Labels, Paper, and Office Machines.
* Promote Office Supplies and Technology in Q4 when sales surge.
* Introduce seasonal kits or bundles for high-margin items.

### Deepen High-Value Customer Relationships

* Offer loyalty perks to customers like **Tamara Chand**, who deliver high revenue + high profit.
* Investigate loss-making high-revenue accounts (e.g., **Sean Miller**) to reduce leakage.
* Segment top 20% customers and design premium outreach/retention programs.

### Optimize Shipping Operations

* Standard Class shipping averages \~5.4 days—slowest of all.
* Orders with <3-day delivery yield higher profit margins (+14.2% vs. 12.5%).
* Negotiate new SLAs with logistics partners or explore regional warehouses for Furniture.

### Focus Expansion on High-Return Regions

* **West** and **East** regions account for 61% of revenue and 70% of total profit.
* Expand team presence and marketing campaigns in California, New York, and Texas.
* Reassess operations in the Central region, where margins are weakest.

### Refine Discounting Strategy

* Blanket discounts have a weak negative correlation with profit (–0.22).
* Introduce data-driven, time-limited promotions instead of across-the-board markdowns.
* Set profit margin guardrails for products eligible for discounting.

### Leverage Seasonality

* Launch early campaigns in September to pull sales forward into Q4.
* Create October-exclusive bundles for high-margin product lines.
* Boost marketing during July–August (historically lowest months).

### Empower Sales Reps & Teams

* Share best practices from top-performing teams in the West and East.
* Reward reps based on margin, not just sales volume.
* Launch a “Sales Champion” bonus program with quarterly awards.

