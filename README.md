# Datheon Data Analytics & Power BI Internship

This repository holds my work for the Datheon Data Analytics & Power BI virtual internship. I completed all four tasks in the task pack: two Python analyses (Tasks 1 and 3) and two Power BI dashboards (Tasks 2 and 4). All three datasets are public sample datasets from the task pack, so the results are practice and not the performance of a real company.

Kareemah Abdulhamid Lawal | [LinkedIn](https://linkedin.com/in/kareemah-abdulhamid-3253b6204)

| Task | Project | Tools | Folder |
|---|---|---|---|
| 1 | Superstore retail sales: exploratory data analysis | Python, pandas, Seaborn, Jupyter | `Task1_Superstore_EDA` |
| 2 | Superstore executive sales and profit dashboard | Power BI, DAX, Power Query | `Task2_Superstore_Dashboard` |
| 3 | Telco customer cohort and churn analysis | Python, pandas, Seaborn, Jupyter | `Task3_Telco_Churn_Analysis` |
| 4 | Financial margin and scenario dashboard | Power BI, DAX, Power Query | `Task4_Financial_Dashboard` |

## Task 1: Superstore EDA

I cleaned the raw Superstore file and then looked at seasonality, category profitability, discounts, regions, and returns. The CSV had a salesperson list and a returns list pasted underneath the sales rows, so I separated those first, then removed one duplicate row and filled 11 missing postal codes (all Burlington, Vermont).

Sales came to about $2.30M with $286K profit, a margin of 12.5%. Sales surge from September to December, and November and December alone bring in about 30% of the year. Furniture sells about as much as the other categories but earns only about a 2.5% margin, and Tables and Bookcases make a loss. Discounts above 20% turn almost every order into a loss, so I recommend an approval limit above that level. The Central region has the weakest margin (about 7.9%) and the highest average discount (about 24%), and Texas, Ohio, and Pennsylvania are the main loss-making states. The top 20% of customers account for under half of sales, so revenue does not depend on a few accounts. The West returns about 12% of its orders, roughly four times any other region. The data has no return reasons, so I could not explain it, and it needs a closer look.

## Task 2: Superstore dashboard

A three-page Power BI report (Overview, Products, Regions) built from the cleaned data in `data/superstore_clean.csv`. This file is the cleaned Task 1 data (same cleaning steps) with extra columns for year, month, margin, returned orders, and discount band. The model is a star schema with an Orders fact table and Date, Customer, Geography, and Product dimensions.

The Overview page has KPI cards for total sales, total profit, profit margin, total orders, and year-over-year sales growth, plus monthly sales by year, sales and profit by year, sales by category and segment, and profit margin by region. The Products page shows profit by sub-category, a category and sub-category treemap, and a table of sales, profit, margin, quantity, and average discount. The Regions page covers discounts and returns: profit by state, profit margin by discount band, sales and return rate by region, and a state table of sales and profit. Every page has slicers, page navigation buttons, and an email button.

## Task 3: Telco churn analysis

I grouped customers into tenure cohorts and contract types, built a cohort retention matrix and Kaplan-Meier retention curves, compared churn across customer groups, and finished with retention recommendations.

26.5% of customers have churned (1,869 of 7,043). Month-to-month customers churn at 42.7%, against 11.3% on one-year contracts and 2.8% on two-year contracts, and 55% of all churned customers left within their first 12 months. Fiber optic customers without tech support churn at 49%, compared with 23% for those with it. The highest-risk group is month-to-month, fiber optic customers paying by electronic check: 1,307 customers with a 60% churn rate. The file has no sign-up dates, so the cohorts are tenure bands and not calendar cohorts.

## Task 4: Financial dashboard

A three-page Power BI report (Overview, Performance, Scenario) built on the Microsoft Financial Sample. The model has a Fact_Financials table, a Date table, a waterfall table, and four what-if parameter tables.

The Overview page shows gross sales, discounts, net sales, COGS, profit, and margin; quarterly net sales, COGS, and profit; a waterfall from gross sales to profit; profit margin by quarter; and net sales by country and segment. The Performance page shows profit by segment, margin and COGS by product, and a segment-by-product margin table. On the Scenario page, you can change units sold, discount, and unit cost and set a target margin, and the dashboard compares scenario profit and margin with the actual figures.

Net sales were $118.7M and profit $16.9M, a margin of 14.2%. Every loss-making row sits in the Enterprise segment, which has a margin of -3.1%.

## Problems I found in the data

The Superstore file had two lists pasted under the sales data: one duplicate row and 11 missing postal codes (the postal code I used for Burlington is an assumption). In the Telco file, 11 customers have a blank total charges value and a tenure of 0, so I set their total charges to 0 and left them out of the retention curves. The Financial Sample has no budget column, so the Scenario page compares scenario against actual and actual margin against a target margin that I can adjust, which is not the same as a budget variance. It also covers only September 2013 to December 2014, so I did not show year-over-year growth there, and its COGS does not equal units sold times manufacturing price.

## How to run

For the notebooks, install Python 3 and run `pip install pandas numpy matplotlib seaborn jupyter`. Open a notebook from its own folder in Jupyter and run all cells. The data is read from the `data` folder.

For the dashboards, open the `.pbix` files in Power BI Desktop. The data is imported into the files, so they open without the source. To refresh them, point the data source in Power Query to your copy of the files in `data`.

## Folder structure

```
├── data/                          source and cleaned datasets
├── Task1_Superstore_EDA/          notebook
├── Task2_Superstore_Dashboard/    Power BI file and screenshots
├── Task3_Telco_Churn_Analysis/    notebook and retention matrix image
└── Task4_Financial_Dashboard/     Power BI file and screenshots
```

## Tools

Python, pandas, Matplotlib, Seaborn, Jupyter, Power BI Desktop, DAX and Power Query. I used an AI assistant (Claude) for guidance and for checking my calculations.
