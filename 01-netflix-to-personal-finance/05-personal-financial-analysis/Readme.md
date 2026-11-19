# Personal Financial Analysis System Project

## Problem Overview
Build a data cleaning and financial analytics pipeline using **Pandas** and **NumPy** to process messy transaction records, calculate net savings, break down category spending, and compute expense statistics.

## Dataset
A structured Python dictionary converted into a Pandas DataFrame containing 15 raw transaction records across four columns (`date`, `type`, `category`, `amount`), including real-world data anomalies such as `"Invalid Date"` strings, negative values (`-5000`), and missing values (`np.nan`).

## Objectives
1. **Load Data:** Convert the raw transaction dictionary into a Pandas DataFrame (`pd.DataFrame`).
2. **Clean Data:** Parse dates safely using `errors='coerce'`, drop `NaT` date rows, and filter out non-positive or `NaN` amounts (`amount > 0`).
3. **Calculate Monthly Savings:** Group transactions by `type`, safely extract total income and expenses, and compute net savings (`Income - Expense`).
4. **Analyze Category Spending:** Isolate `"Expense"` rows, aggregate spending by `category`, and sort from highest to lowest expense.
5. **Compute Statistical Insights:** Convert expense amounts into a NumPy array to calculate mean, median, maximum, minimum, and standard deviation.

## Key Learnings & Notes
* **Safe Date Parsing (`pd.to_datetime(df['date'], errors='coerce')`):** Using `errors='coerce'` prevents crashes on malformed strings like `"Invalid Date"` by converting them into `NaT` values so they can be dropped cleanly.
* **Targeted Row Dropping (`df.dropna(subset=['date'])`):** Passing `subset=['date']` drops only rows where date parsing failed without accidentally deleting rows needed for later cleaning steps.
* **Boolean Indexing vs. Column Selection:** `df['Expense']` looks for a column header and raises a `KeyError`, whereas `df[df['type'] == 'Expense']` filters rows based on cell values inside the `'type'` column.
* **Safe Dictionary Lookups (`summary.get('Income', 0)`):** Using `.get()` prevents `KeyError` crashes if a dataset has zero transactions for either `"Income"` or `"Expense"`.
* **Grouping & Resetting Index:** Chaining `.groupby('category')['amount'].sum().sort_values(ascending=False).reset_index()` turns grouped Series results back into a clean two-column DataFrame.
* **Scalar Values in DataFrames:** Passing single numbers (scalars) directly into `pd.DataFrame()` triggers `ValueError: If using all scalar values, you must pass an index`—always wrap scalar values in lists (`{"Col": [val]}`) or wrap a single dictionary in brackets (`pd.DataFrame([insights])`).
