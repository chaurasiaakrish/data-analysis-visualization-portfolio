# Fitness Activity Data Analysis Project

## Problem Overview
Build a numerical fitness tracker analysis script using **NumPy** to simulate daily step counts, reshape 1D activity data into a 2D weekly matrix, compute row-wise totals and averages, identify peak activity days, and sort step records.

## Dataset
A synthetically generated 1D NumPy array of 7 random integers (`np.random.randint`) representing daily step counts between `3000` and `12000` across one week.

## Objectives
1. **Generate Step Data:** Create a 1D NumPy array of 7 random daily step counts between `3000` and `12000`.
2. **Reshape Weekly Matrix:** Convert the 1D array into a 2D `1x7` matrix (`1` week × `7` days) using `np.reshape()`.
3. **Analyze Weekly Metrics:** Compute total weekly steps and daily average steps across the matrix row (`axis=1`).
4. **Identify Peak Activity:** Locate the exact day indices (`0`–`6`) for the most active and least active days using `np.argmax()` and `np.argmin()`.
5. **Sort Activity Records:** Return daily step counts sorted in ascending order using `np.sort()`.

## Key Learnings & Notes
* **Random Array Generation (`np.random.randint(low, high, size)`):** `randint` lives inside NumPy's `.random` submodule and takes `(min, max, count)` in that exact order.
* **Row-Wise Operations (`axis=1`):** Passing `axis=1` on a `1x7` matrix computes metrics horizontally across all 7 days of the week and returns a 1-element array, requiring `` at the end to extract the clean scalar value.
* **Index vs. Value Functions (`argmax`/`argmin` vs. `max`/`min`):** `np.argmax()` and `np.argmin()` return the zero-based position of extreme values rather than the step counts themselves, and should be called on the 1D `steps` array without `axis=1`.
* **Non-Destructive Sorting (`np.sort(steps)`):** Returns a sorted copy of the array in ascending order while keeping the original day-by-day order intact.
