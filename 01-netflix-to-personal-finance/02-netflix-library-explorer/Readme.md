# Netflix Library Explorer Project

## Problem Overview
Build an exploratory data analysis (EDA) tool using **Pandas** to inspect, filter, and summarize content trends from the Netflix catalog dataset.

## Dataset
A CSV dataset (`netflix.csv`) containing Netflix titles along with key attributes such as:
`title`, `type`, `release_year`, and `rating`

## Objectives
1. **Load Data:** Read `netflix.csv` into a Pandas DataFrame and preview the first 5 rows (`title`, `type`, `release_year`).
2. **Explore Dataset:** Inspect the total dimensions (`shape`) and column names of the DataFrame.
3. **Count Content Types:** Calculate the distribution of `Movie` vs. `TV Show` entries.
4. **Filter Recent Content:** Extract titles released after `2015` using boolean indexing.
5. **Analyze Ratings:** Identify and display the top 5 most common content ratings.
6. **Sort Catalog:** Order the dataset by `release_year` in descending order to highlight the latest additions.

## Key Learnings & Notes
* **Double Square Brackets (`df[['col1', 'col2']]`):** Selecting multiple columns requires passing a Python list inside outer brackets—single brackets with commas raise a `KeyError`, and keyword arguments like `columns=` are not valid inside `[]`.
* **Value Counts Method:** Used `df['col'].value_counts()` (note the `s` at the end of `counts`) to count unique category frequencies in descending order.
* **Boolean Indexing:** Filtered rows cleanly using `df[df['release_year'] > 2015]`.
* **Sorting DataFrames:** Used `df.sort_values(by='release_year', ascending=False)` on the full DataFrame rather than `.sort()` on a single Series so all columns stay aligned.
* **Converting `df.columns` to `list()`:** Wrapping `list(df.columns)` converts the Pandas `Index` object into a standard Python list, preventing `The truth value of an array with more than one element is ambiguous` errors during automated equality checks.
