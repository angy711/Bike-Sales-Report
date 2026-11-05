# Bike Sales Dashboard (Excel)

An interactive Excel dashboard that explores which customer groups buy bikes, built with data cleaning, PivotTables, PivotCharts and slicers.

![Dashboard preview](Dashboard.png)

## Business Problem

A bike retailer wants to know **who buys its bikes** so it can target marketing and sales efforts better. This dashboard answers questions such as:

- Which customer segments (age, gender, marital status, education, region) are most likely to buy a bike?
- Does income differ between customers who bought a bike and those who did not?
- Does commute distance relate to buying a bike?
- Which age groups should campaigns focus on?

## Dataset

Customer-level data with one row per customer.

| Column | Description |
|---|---|
| ID | Unique customer ID |
| Marital Status | Married / Single |
| Gender | Female / Male |
| Income | Annual income |
| Children | Number of children |
| Education | Highest education level |
| Occupation | Job category |
| Home Owner | Yes / No |
| Cars | Number of cars owned |
| Commute Distance | Distance bands (0-1, 1-2, 2-5, 5-10, 10+ miles) |
| Region | Europe / North America / Pacific |
| Age | Customer age |
| **Age Brackets** | *Derived from Age:* Adult / Mid-Age / Old |
| Purchased Bike | Yes / No (target variable) |

## Process

1. **Data cleaning**
   - Removed duplicate records (by ID)
   - Checked every column for blanks and inconsistent labels
   - Converted the data into an Excel Table so PivotTables resize on refresh
2. **Feature engineering**
   - Created an `Age Brackets` column from `Age` (Adult, Mid-Age, Old)
3. **Analysis with PivotTables**
   - Average income by gender and purchase status
   - Number of purchases by age bracket
   - Number of purchases by commute distance
   - **My own addition:** purchase rate (% of customers who bought) per age bracket and commute distance, using *Show Values As → % of Row Total*
4. **Dashboard**
   - PivotCharts linked to the PivotTables
   - Slicers for Marital Status, Region and Education to filter all charts at once

## Dashboard Contents

| Chart | Question it answers |
|---|---|
| Average Income per Purchase | Do buyers earn more or less than non-buyers, by gender? |
| Customer Age Bracket | Which age groups buy bikes most often? |
| Customer Commute | How does commute distance relate to buying a bike? |

## My Additions Beyond the Tutorial

The dashboard layout follows a YouTube tutorial (see Credits). I extended it with:

- Two extra PivotTables showing the **purchase rate** (% of row total) by age bracket and by commute distance. Counts alone can be misleading when groups differ in size. For example, the 0-1 mile group has the most buyers, but the 2-5 mile group has the highest purchase rate.
- Removal of duplicate records and a check for blanks before building the PivotTables, plus the fix for stale "(blank)" slicer items.
- The business framing, key insights, recommendations and limitations in this README.

## Key Insights

All figures are for the full dataset (no slicer filters applied).

- **Income:** Customers who bought a bike have a higher average income than those who did not, for both genders (women: 55,774 € vs 53,440 €; men: 60,124 € vs 56,208 €). The difference is modest, so income alone is not a strong predictor.
- **Age:** Mid-Age customers are by far the largest segment and the only age group where buyers outnumber non-buyers. Older customers are much less likely to buy.
- **Commute distance:** The 0-1 mile group has the most buyers in absolute terms (200 of 366 customers). Beyond 5 miles, non-buyers clearly outnumber buyers (5-10 miles: 76 vs 116; more than 10 miles: 33 vs 78).
- **Purchase rate by age:** Overall, 48.1% of the 1,000 customers bought a bike. The rate is highest for Mid-Age customers (53.2%), followed by Adults (42.2%) and Old customers (31.2%).
- **Purchase rate by commute distance:** The rate is highest for customers with a 2-5 mile commute (58.6%), followed by 0-1 miles (54.6%) and 1-2 miles (45.6%). It falls for longer commutes: 39.6% for 5-10 miles and only 29.7% for more than 10 miles.

> These are associations in the data, not proof of cause and effect.

## Recommendations

- Focus campaigns on Mid-Age customers, the largest group with a slight tilt towards buying.
- Target customers with commutes up to 5 miles, especially 0-1 miles (largest buyer group) and 2-5 miles (highest purchase rate).
- Review the offer for older customers and long-distance commuters, where purchase rates are lowest (for example, models better suited to them).
- Consider income in targeting, but as a secondary factor given the small gap.

## Tools

- Microsoft Excel: PivotTables, PivotCharts, Slicers, Tables, data cleaning

## Challenges and Learnings

- Removing duplicates after building the PivotTables left stale "(blank)" items in the slicers. Fixed by refreshing the PivotTables and enabling *Hide items with no data* in the slicer settings.
- Lesson learned: clean the raw data first, and base PivotTables on an Excel Table.

## Limitations

- The data shows correlations, not causes, and no statistical tests were run.
- The dataset has only 1,000 customers, so results may not generalize.
- Purchase rates were calculated per variable; combined effects (for example age and commute together) were not analysed.
- Age brackets are my own definition, and other cut-offs could change the picture.

## Files

- `Bike_Sales_Dashboard.xlsx`: cleaned data, PivotTables and dashboard
- `Dashboard.png`: dashboard screenshot

## Credits

The dataset and the base dashboard (income, age bracket and commute charts with slicers) are based on a YouTube tutorial: [https://www.youtube.com/watch?v=zXnQNytHCPM&t=9300s]. The purchase-rate PivotTables, the analysis and this documentation are my own work.
