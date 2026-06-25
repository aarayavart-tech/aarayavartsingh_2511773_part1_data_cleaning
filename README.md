# Part 1: Business Data Cleaning, Validation & Excel Reporting

## Problem Summary

The retail company exported order-level sales data from multiple systems. The dataset contained data quality issues including inconsistent text formatting, missing values, duplicate records, invalid discounts, inconsistent date formats, and order status inconsistencies.

The objective was to clean, validate, and prepare the dataset for business reporting and analysis.

---

## Dataset Description

**Source File:** raw_orders.xlsx

**Total Records (Raw):** 932

**Columns:** 21

Major fields include:

* order_id
* order_date
* ship_date
* customer_name
* segment
* region
* state
* city
* category
* sub_category
* ship_mode
* quantity
* unit_price
* discount
* sales
* cost
* profit
* payment_status
* order_status

---

## Tools Used

* Microsoft Excel
* Pivot Tables
* Data Validation
* Excel Formulas
* Conditional Formatting

---

## Cleaning Steps Performed

### Text Standardization

Cleaned and standardized:

* customer_name
* segment
* region
* state
* city
* category
* sub_category
* ship_mode
* payment_status
* order_status

Methods used:

* TRIM
* SUBSTITUTE
* Find & Replace
* Proper Case Conversion

### Date Cleaning

Standardized:

* order_date
* ship_date

Validated:

* Missing dates
* Invalid date formats
* Ship date before order date

Created:

* shipping_delay_days

### Missing Values

Handled:

* Missing region → Unknown
* Missing ship_mode → Unknown
* Missing discount → 0 when other sales fields were valid

### Duplicate Handling

Reviewed:

* Exact duplicate rows
* Duplicate order IDs

Conflicting records were flagged for review.

### Business Rule Validation

Validated:

* Negative discounts
* Invalid shipping dates
* Failed payments
* Cancelled orders
* Refunded orders

---

## Data Quality Issues Found

| Issue                       | Count |
| --------------------------- | ----- |
| Missing Region              | 26    |
| Missing Ship Mode           | 22    |
| Missing Discount            | 18    |
| Exact Duplicate Rows        | 20    |
| Negative Discounts          | 16    |
| Ship Date Before Order Date | 2     |

---

## Calculated Columns Added

* cleaned_discount
* calculated_sales
* calculated_profit
* profit_margin
* shipping_delay_days
* order_month
* order_year
* data_quality_flag

---

## Pivot Reports Created

1. Sales and Profit by Region
2. Sales and Profit by Category & Sub-Category
3. Order Count by Ship Mode
4. Profit Margin by Segment
5. Refunded / Cancelled / Failed Orders by Region
6. Monthly Sales Trend

---

## Key Business Insights

* Most orders were completed successfully.
* Some records contained negative discount values requiring review.
* Missing region and shipping information existed in multiple records.
* Duplicate transactions were present and required validation.
* Refunded and failed payment orders were separated from completed sales analysis.

---

## Assumptions and Limitations

* Missing discounts were treated as zero only when other financial fields were valid.
* Invalid discounts were flagged rather than corrected automatically.
* Conflicting duplicate orders were not deleted automatically.
* Original raw dataset remained unchanged.

---

## Screenshots Included

* raw_data_preview.png
* cleaned_data_preview.png
* pivot_summary_1.png
* pivot_summary_2.png
