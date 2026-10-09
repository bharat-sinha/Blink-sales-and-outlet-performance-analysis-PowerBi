# Blinkit Sales & Outlet Performance Dashboard (Power BI)

![Blinkit Power BI dashboard](Blinkit%20dashboard%20powerbi.png)

An interactive Power BI dashboard that shows where Blinkit's grocery sales come from, broken down by outlet size, location tier, outlet age and product category. It is built on a practice dataset of about 8.5K item records and about $1.2M in sales.

**Tools:** Power BI (Power Query, data modeling, DAX), Excel (initial cleaning)
**Domain:** Retail analytics, quick commerce / FMCG

---

## Business problem

A retail manager wants to know which outlet formats, locations and product categories drive revenue, so that expansion and assortment decisions rest on data and not on instinct.

## Questions the dashboard answers

1. How much do we sell overall, and what does a typical item record bring in?
2. Which outlet size contributes the most sales?
3. Which location tier (Tier 1, 2, 3) generates the most revenue?
4. Which item categories carry the business?
5. How do low-fat and regular products compare?
6. How have outlets opened between 2012 and 2022 performed?
7. How satisfied are customers (average rating)?

## Dataset

- **Source:** BlinkIT Grocery Data (a public practice dataset, included in this repo as `BlinkIT Grocery Data.xlsx`)
- **Size:** about 8.5K item records
- **Main fields:** item type, fat content, outlet size, outlet location tier, outlet type, outlet establishment year, sales, rating
- **Note:** this is a sample dataset, not real Blinkit company data.

## Approach

1. **Clean** the raw file in Excel and Power Query: standardize fat-content labels, check for blanks and duplicates, fix data types.
2. **Model** the data in Power BI and build the DAX measures below.
3. **Visualize** the KPIs, breakdowns and trends, with slicers for outlet location tier, outlet size and item type.
4. **Interpret** the results and write recommendations (see below).

## Key measures (DAX)

```DAX
Total Sales   = SUM ( 'BlinkIT Grocery Data'[Sales] )
Avg Sales     = AVERAGE ( 'BlinkIT Grocery Data'[Sales] )
No. of Items  = COUNTROWS ( 'BlinkIT Grocery Data' )
Avg Rating    = AVERAGE ( 'BlinkIT Grocery Data'[Rating] )
Sales % Total = DIVIDE ( [Total Sales], CALCULATE ( [Total Sales], ALL ( 'BlinkIT Grocery Data' ) ) )
```

## Key findings

| Metric | Result |
|---|---|
| Total sales | $1.20M |
| Items analyzed | 8.52K |
| Average sales per item record | $140.99 |
| Average customer rating | 3.9 |
| Top outlet size | Medium, about 42% of sales |
| Top location tier | Tier 3, about $472K (roughly 39% of sales) |
| Top categories | Fruits & Vegetables, Snack Foods, Household |

Read these as patterns in the sample data, not as proven causes.

## Recommendations

These are hypotheses for a business team to test, based on what the dashboard shows.

1. **Prioritize medium-size outlets when planning new stores.** They produce the largest share of sales. Before acting, check sales per outlet, because a large share could simply mean there are more medium outlets.
2. **Look closely at Tier 3 locations.** They lead in total sales. Compare sales per outlet across tiers to see whether Tier 3 is truly more productive or just larger in number.
3. **Protect stock and visibility for the top three categories.** Fruits & Vegetables, Snack Foods and Household drive the most revenue, so availability gaps there cost the most.
4. **Investigate the 3.9 average rating.** Find which outlets or categories pull it down before it affects repeat purchases.

## Limitations

- The dataset has no cost, margin or profit data, so I can describe revenue but not profitability.
- Sales are summarized per item record. This is not transaction-level data, so I did not analyze daily or seasonal patterns.
- The dataset is a sample, so results should not be generalized to the real company.

## Next steps

- Add sales per outlet and sales per item type as measures, to separate size effects from efficiency.
- Test the relationship between item visibility and sales.
- Add margin data to move from revenue reporting to profit analysis.

## Skills demonstrated

Data cleaning (Power Query, Excel) · Data modeling · DAX measures · KPI design · Interactive dashboards with slicers · Turning findings into business recommendations

## Repository contents

```
├── BlinkIT Grocery Data.xlsx        # raw dataset
├── blinkit dashboard.pbix           # Power BI file (open in Power BI Desktop)
├── Blinkit dashboard powerbi.png    # dashboard screenshot
├── blinkit analysis bi.pdf          # exported report
└── README.md
```

**To explore:** download `blinkit dashboard.pbix` and open it in Power BI Desktop (free). Use the slicers to filter by location tier, outlet size and item type.

## Related project

The same dataset analyzed with Excel pivot tables and slicers: [BlinkIt-Sales-and-Outlet-Performance-Analysis-Excel](https://github.com/bharat-sinha/BlinkIt-Sales-and-Outlet-Performance-Analysis-Excel)

## Author

**Bharat Sinha**, aspiring data analyst
[LinkedIn](https://www.linkedin.com/in/bharat-sinha-122791130/) | [GitHub](https://github.com/bharat-sinha) | sinha.bharat8@gmail.com
