# Zepto Inventory Analytics

SQL analysis of an e-commerce inventory dataset to examine product availability, pricing, discounts, and category-level inventory value.

## Business questions

- Which categories have the most out-of-stock listings?
- Which products and categories offer the largest discounts?
- What is the listed inventory value by category?
- How does price per gram vary across products?

## Tools and files

**PostgreSQL · SQL · CSV**

| File | Purpose |
| --- | --- |
| `Zepto_SQL_data_analysis.sql` | Table definition, exploration, cleaning, and business analysis queries |
| `zepto_v2.csv` | Source product inventory dataset |

## Analysis approach

1. Define the inventory table and import the CSV.
2. Profile records, missing values, categories, stock status, and repeated product names.
3. Inspect zero-price records, remove rows with zero MRP, and convert prices from paise to rupees.
4. Compare discounts, stock availability, price per gram, weight bands, and category totals.

Repeated product names are reviewed rather than automatically removed, because different listings can represent different package sizes or variants.

## Run locally

1. Create a PostgreSQL database and connect using pgAdmin or `psql`.
2. Run only the initial table-creation section of `Zepto_SQL_data_analysis.sql`.
3. Import `zepto_v2.csv` into `zepto`, mapping the CSV fields to their matching columns and excluding the generated `sku_id`.
4. Run the exploration, cleaning, and analysis sections in order.

The script starts by dropping the existing `zepto` table. Use a dedicated project database. The price conversion updates stored values; run it once per fresh import.

## Interpretation

`discountedSellingPrice * availableQuantity` estimates listed inventory value at the selling price. It is not realized sales revenue. This snapshot does not support claims about customer retention, conversion, or revenue trends over time.

## Source and license

Adapted from [Amlan Mohanty's Zepto SQL project](https://github.com/amlanmohanty1/zepto-SQL-data-analysis-project). The original copyright and MIT license are retained in [LICENSE](LICENSE). This repository contains the imported analysis and revised documentation.
