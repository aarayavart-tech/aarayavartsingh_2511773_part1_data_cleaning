# Cleaning Log

## Project

Business Data Cleaning, Validation & Excel Reporting

---

## 1. Issues Identified

### Text Formatting Issues

The following columns contained inconsistent formatting:

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

Issues found:

* Leading spaces
* Trailing spaces
* Multiple consecutive spaces
* Mixed uppercase and lowercase values
* Inconsistent category naming

---

### Missing Values

Missing values were detected in:

* region
* ship_mode
* discount
* date fields (where applicable)

---

### Date Issues

The following date-related issues were checked:

* Missing order dates
* Missing ship dates
* Invalid date formats
* Ship dates occurring before order dates

---

### Duplicate Records

The dataset was checked for:

* Exact duplicate rows
* Duplicate order IDs
* Duplicate order IDs with conflicting information

---

### Discount Validation Issues

The following discount issues were validated:

* Missing discount values
* Negative discounts
* Discounts exceeding the allowed range

---

### Order Status Issues

The following statuses were reviewed:

* Completed
* Cancelled
* Refunded
* Failed Payment

---

## 2. Cleaning Actions Performed

### Text Standardization

Applied:

* TRIM()
* SUBSTITUTE()
* Find and Replace
* Proper Case formatting

Results:

* Removed unnecessary spaces
* Standardized text capitalization
* Corrected inconsistent category names
* Improved reporting consistency

---

### Missing Value Handling

#### Region

Business Rule Applied:

Missing region values were replaced with:

Unknown

#### Ship Mode

Business Rule Applied:

Missing ship mode values were replaced with:

Unknown

#### Discount

Business Rule Applied:

Missing discounts were treated as 0 only when all related sales fields were valid.

---

### Date Standardization

Actions Performed:

* Converted order_date to a consistent date format
* Converted ship_date to a consistent date format
* Validated date integrity
* Flagged invalid records

Created:

shipping_delay_days

Formula:

Ship Date − Order Date

---

### Duplicate Handling

Actions Performed:

* Identified exact duplicate rows
* Identified duplicate order IDs
* Removed exact duplicates where appropriate
* Flagged conflicting duplicate records for manual review

Conflicting duplicates were not deleted automatically.

---

## 3. Business Rules Applied

### Rule 1

Missing Region

Action:

Filled with "Unknown"

---

### Rule 2

Missing Ship Mode

Action:

Filled with "Unknown"

---

### Rule 3

Missing Discount

Action:

Converted to 0 only when other sales values were valid

---

### Rule 4

Negative Discount

Action:

Flagged as Invalid

---

### Rule 5

Discount Above Allowed Range

Action:

Flagged as Invalid

---

### Rule 6

Cancelled Orders

Action:

Excluded from completed sales summaries

---

### Rule 7

Failed Payments

Action:

Excluded from completed sales summaries

---

### Rule 8

Refunded Orders

Action:

Reported separately in summary reports

---

### Rule 9

Ship Date Before Order Date

Action:

Flagged as Invalid Shipping Record

---

## 4. Calculated Columns Created

The following calculated columns were added:

* cleaned_discount
* calculated_sales
* calculated_profit
* profit_margin
* shipping_delay_days
* order_month
* order_year
* data_quality_flag

---

## 5. Data Quality Flags

### Clean

Record passes all validation checks.

### Warning

Record contains minor issues but remains usable.

### Invalid

Record violates business rules and requires review.

---

## 6. Assumptions

* Unknown values were allowed for region and ship mode.
* Missing discounts could be treated as 0 when financial fields were valid.
* Duplicate order conflicts require business review.
* Invalid discounts were not automatically corrected.

---

## 7. Records Removed

* Exact duplicate records were removed where confirmed duplicates existed.

---

## 8. Records Flagged

Records were flagged for:

* Invalid discounts
* Invalid dates
* Duplicate order conflicts
* Missing critical business information

---

## 9. Limitations

* Source system errors cannot be independently verified.
* Some business decisions require domain expert review.
* Flagged records may require manual investigation before final reporting.

---

## Cleaning Completed Successfully

Final output files generated:

* cleaned_orders.xlsx
* data_quality_report.xlsx
* pivot_summary.xlsx
* cleaning_log.md

Dataset is ready for business analysis and reporting.
