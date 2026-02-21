In this application, the categorization happens in a two-step process, combining machine learning with a specific business rule.

Here is exactly how the criteria works:

Step 1: Grouping by Overall Similarity (The Machine Learning part)
First, the K-Means algorithm looks at all the financial ratios for every bank across the years. It plots them mathematically and groups them into 3 distinct clusters based on their overall similarity. At this stage, the clusters don't have names; they are just Groups A, B, and C.

Step 2: Ranking into Categories (The Criteria part)
Once the 3 groups are formed, the algorithm needs to decide which group gets which label. It does this by calculating the "average" financial health of each group.

It searches your dataset's columns to find a primary profitability indicator in this strict order of preference:

Return on assets (ROA)

If ROA isn't found, it looks for Return on equity (ROE).

If ROE isn't found, it looks for Operating profit.

(Fallback: If none of those are in your file, it just uses the very first numerical column).

It then looks at the average score of that specific metric for each of the 3 groups and assigns the labels like this:

Critical (Red): Assigned to the group with the lowest average score in that metric.

Balanced (Amber): Assigned to the group with the middle average score.

Healthy (Green): Assigned to the group with the highest average score.

In summary: The banks are grouped together based on all their data points being similar, but the actual labels (Critical, Balanced, Healthy) are awarded based on which group has the worst, middle, and best average Return on Assets (or a similar profitability metric).
