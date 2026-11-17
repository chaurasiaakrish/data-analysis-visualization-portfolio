# Exam Marks Statistics Project

## Problem Overview
Build an analytics tool using **NumPy** to evaluate student exam performance from raw numerical scores.

## Dataset
A 1D NumPy array containing 10 student exam scores:
`[78, 85, 33, 66, 15, 88, 90, 59, 29, 70]`

## Objectives
1. **Load Data:** Store the exam scores in a NumPy array.
2. **Compute Statistics:** Calculate the class mean, median, and standard deviation.
3. **Analyze Performance:** Filter students scoring above the class average and identify students scoring below the pass threshold (`< 35`).
4. **Find Extremes:** Identify the highest and lowest scores in the class.

## Key Learnings & Notes
* Used `np.mean()`, `np.median()`, and `np.std()` for quick statistical summaries.
* Used Python list comprehensions to filter scores based on dynamic thresholds.
