---
layout: default
title: "One-hot Encoding"
---
One-hot encoding is a technique for creating a numerical representation of categorical features. It generates new binary features (columns) for each category, where each takes the value 0 or 1, indicate whether an observation belongs to that category (1: true, 0: false).

For example:

| smoking_status &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| sex&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | age |
| --- | --- | --- |
| never smoked | F | 23 |
| currently smoke | F | 43 |
| smoked before | M | 37 |
| currently smoke | M | 25 |
| never smoked | M | 32 |

We can convert this dataset into the following form using one-hot encoding:

| never_smoked &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| currently_smoke &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| smoked_before&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | sex&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | age |
| --- | --- | --- | --- | --- |
| 1 | 0 | 0 | 0 | 23 |
| 0 | 1 | 0 | 0 | 43 |
| 0 | 0 | 1 | 1 | 37 |
| 0 | 1 | 0 | 1 | 25 |
| 1 | 0 | 0 | 1 | 32 |

Note: sex is also converted to 0s and 1s (0: female, 1: male).