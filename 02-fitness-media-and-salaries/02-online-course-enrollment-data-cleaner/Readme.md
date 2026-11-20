# Online Course Enrollment Data Cleaner Project

## Problem Overview
Build an end-to-end data cleaning and feature-engineering pipeline using **Pandas** to inspect raw Udemy course enrollment records, impute and drop missing values, deduplicate entries, normalize text formatting and data types, engineer a revenue estimate metric, and export the cleaned dataset.

## Dataset
`udemy_courses.csv` containing online course catalog records, including key attributes such as:
`course_title`, `subject`, `price`, `num_subscribers`, and `num_lectures`

## Objectives
1. **Load & Inspect Data:** Import `udemy_courses.csv` and examine column data types, non-null counts, and summary statistics using `df.info()` and `df.describe()`.
2. **Handle Missing Values:** Impute missing `course_title` entries with `"Unknown Course"`, fill missing `num_subscribers` with `0`, and drop rows missing critical `price` or `num_lectures` values.
3. **Deduplicate Records:** Remove duplicate courses sharing the same `['course_title', 'subject']` combination while keeping the `'first'` occurrence.
4. **Normalize Strings & Data Types:** Strip extra whitespace and standardize `course_title` and `subject` to Title Case, then cast `price` to `float` and `num_subscribers` to `int`.
5. **Feature Engineering & Export:** Calculate a derived `revenue_estimate` column (`price * num_subscribers`) and export the cleaned table to `cleaned_udemy_courses.csv` without row index numbers (`index=False`).

## Key Learnings & Notes
* **Targeted Row Dropping (`df.dropna(subset=['price', 'num_lectures'])`):** The parameter name is strictly singular (`subset=`), checking only the specified columns so incomplete rows are removed without slicing away other columns.
* **String Accessor Chaining (`.str.strip().str.title()`):** In Pandas, `.str` must precede **every** string method in a chain because `.str.strip()` returns a Series rather than a raw Python string.
* **Direct Type Casting (`.astype(float)` / `.astype(int)`):** Once missing values are cleaned, `.astype()` cleanly converts columns to standard 64-bit numeric types (`float64` and `int64`).
* **Clean CSV Export (`df.to_csv(..., index=False)`):** Passing `index=False` prevents Pandas from writing an extra unnamed row-index column into the exported CSV file.
