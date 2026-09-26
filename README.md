# Blinkit Grocery Sales Dashboard — Power BI

An interactive Power BI dashboard that breaks down **1.20M in grocery sales across 8,523 items and 10 outlets**. It shows which products, store formats and city tiers actually drive revenue for a quick-commerce grocery business.



---

## The Problem

Quick-commerce grocery runs on thin margins. Deciding which categories to push, which store formats to open and which city tiers to expand into needs more than a sales total. This dashboard answers these five questions on a single screen:

1. Which item categories generate the most revenue?
2. How does fat content (Low Fat vs Regular) affect sales, and does that hold across city tiers?
3. Which outlet sizes, types and locations perform best?
4. Does outlet age affect sales performance?
5. How do customer ratings and item visibility relate to outlet performance?

---

## Key Insights

| Metric | Value |
|---|---|
| Total Sales | **1.20M** |
| Average Sales per Item | **141** |
| Number of Items | **8,523** |
| Average Rating | **3.97** |

- **Fruits & Vegetables and Snack Foods lead**, together accounting for about 30% of total sales. Household and Frozen Foods follow.
- **Low Fat products bring in 65% of revenue**, almost double the share of Regular products.
- **Tier 3 cities are the strongest market** at 39% of sales, ahead of Tier 2 (33%) and Tier 1 (28%). Smaller cities are outselling metros here.
- **Medium-sized outlets beat large ones.** Medium outlets contribute 42% of sales and High (large) outlets only 21%, so bigger stores don't mean more revenue.
- **Supermarket Type 1 dominates** with about 66% of total sales, more than the other three outlet types combined.
- **The 1998 outlets are the top earners** at about 205K. Sales from outlets opened after 2000 are flat at roughly 130K per cohort, which suggests newer stores reach a ceiling quickly.

---

## Dashboard Features

- **KPI cards** for Total Sales, Average Sales, Number of Items and Average Rating
- **Dynamic metric switching:** a field-parameter slicer lets you swap every chart between Total Sales, Avg Sales, Item Count and Avg Rating without duplicating visuals
- **Slicers** for Outlet Location Type, Outlet Size and Item Type
- **Visuals used:**
  - Donut chart for sales by fat content and by outlet size
  - Bar chart for sales by item type
  - Clustered bar chart for fat content by outlet tier
  - Line chart for sales trend by outlet establishment year
  - Funnel chart for sales by outlet location tier
  - Matrix table for all KPIs broken down by outlet type
- Custom Blinkit-inspired yellow/green theme with a designed background

---

## Dataset

| Column | Description |
|---|---|
| Item Identifier | Unique product ID |
| Item Type | Product category (16 categories) |
| Item Fat Content | Low Fat / Regular |
| Item Weight | Product weight |
| Item Visibility | Share of display area allocated to the product |
| Outlet Identifier | Unique store ID (10 outlets) |
| Outlet Establishment Year | Year the outlet opened (1998–2022) |
| Outlet Size | Small / Medium / High |
| Outlet Location Type | Tier 1 / Tier 2 / Tier 3 |
| Outlet Type | Grocery Store, Supermarket Type 1/2/3 |
| Total Sales | Sales value for the item |
| Rating | Customer rating (1–5) |

**Size:** 8,523 rows × 12 columns

### Data Cleaning

- Standardised inconsistent fat-content labels. `LF` and `low fat` became **Low Fat**, and `reg` became **Regular**, which reduced 5 raw categories to 2.
- Handled 1,463 missing `Item Weight` values.
- Flagged 526 items with zero visibility as data-quality issues.

---

## DAX Measures

```DAX
Total Sales = SUM('Blinkit Grocery Data'[Total Sales])

Avg Sales = AVERAGE('Blinkit Grocery Data'[Total Sales])

No of Items = COUNT('Blinkit Grocery Data'[Item Identifier])

Avg Rating = AVERAGE('Blinkit Grocery Data'[Rating])
```

---

## Tools Used

- **Power BI Desktop** for data modelling, DAX and visualisation
- **Power Query** for data cleaning and transformation
- **DAX** for measures and field parameters

---

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/blinkit-sales-dashboard.git
   ```
2. Open `BLINKIT_DASHBOARD_POWERBI.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free).
3. If prompted, point the data source to `blinkit_Grocery_Data.csv` in the repo folder.
4. Use the slicers and the metric switcher to explore.

---

## Repository Structure

```
blinkit-sales-dashboard/
├── BLINKIT_DASHBOARD_POWERBI.pbix   # Power BI report
├── blinkit_Grocery_Data.csv         # Raw dataset
├── assets/
│   └── dashboard.png                # Dashboard screenshot
└── README.md
```

---

## Author

**Dhruv Hooda** —(dhruvh.work@gmail.com)
