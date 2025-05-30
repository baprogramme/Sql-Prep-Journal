# CVS Health - Pharmacy Sales Profit Analysis

CVS Health is trying to better understand its pharmacy sales, and how well different products are selling. Each drug can only be produced by one manufacturer.

---

## Task

Write a query to find the **top 3 most profitable drugs sold**, and how much profit they made.  
Assume that there are **no ties** in the profits.  
Display the result from the **highest to the lowest** total profit.

---

## Definition

- **COGS** stands for *Cost of Goods Sold*, which is the direct cost associated with producing the drug.
- **Total Profit** = **Total Sales** - **Cost of Goods Sold**



---

## `pharmacy_sales` Table Structure

| Column Name | Type      |
|-------------|-----------|
| product_id  | integer   |
| units_sold  | integer   |
| total_sales | decimal   |
| cogs        | decimal   |
| manufacturer| varchar   |
| drug        | varchar   |

---

## Example Input

| product_id | units_sold | total_sales | cogs      | manufacturer | drug             |
|------------|------------|-------------|-----------|--------------|------------------|
| 9          | 37410      | 293452.54    | 208876.01 | Eli Lilly    | Zyprexa          |
| 34         | 94698      | 600997.19    | 521182.16 | AstraZeneca  | Surmontil        |
| 61         | 77023      | 500101.61    | 419174.97 | Biogen       | Varicose Relief  |
| 136        | 144814     | 1084258.00   | 1006447.73| Biogen       | Burkhart         |

---

## Example Output

| drug             | total_profit |
|------------------|--------------|
| Zyprexa          | 84576.53      |
| Varicose Relief  | 80926.64      |
| Surmontil        | 79815.03      |

---

## Explanation

- **Zyprexa** made the most profit ($84,576.53), followed by **Varicose Relief** ($80,926.64) and then **Surmontil** ($79,815.03).
- The dataset you are querying against may have different input & output - this is just an example!

---

## SQL Query

```sql
SELECT drug,(total_sales-cogs) as total_profit FROM 
pharmacy_sales order by 2 desc limit 3;
