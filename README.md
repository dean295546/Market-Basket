# 🛒 Market Basket Analysis with Apriori Algorithm

This project demonstrates a **Market Basket Analysis (MBA)** using the **Apriori algorithm** on a grocery dataset. The goal is to discover frequent itemsets and association rules that can help understand customer purchasing behavior.

## Project Summary

We analyze customer transaction data to:
- Identify frequently bought-together items.
- Generate association rules (e.g., "If customers buy X, they also tend to buy Y").
- Use metrics like **support**, **confidence**, **lift**, and **conviction** to evaluate the strength of these rules.

## Dataset

- Source: [Groceries Dataset on Kaggle](https://www.kaggle.com/datasets/heeraldedhia/groceries-dataset/data)
- Columns:
  - `Member_number`: Customer ID
  - `Date`: Purchase date
  - `itemDescription`: Item bought

> Each row represents a single product bought by a customer on a specific date.

## Methodology

1. **Data Preprocessing**
   - Combine `Member_number` and `Date` to create a unique `purchase_id`.
   - Convert transactions into a one-hot encoded format (basket format).
   - Convert purchase quantity >1 to 1 for binary representation.

2. **Frequent Itemset Mining**
   - Use the **Apriori algorithm** (`mlxtend`) to find item combinations with `min_support = 0.001`.

3. **Association Rule Mining**
   - Generate rules with metrics: `lift`, `confidence`, `support`, etc.
   - Sort rules to find the most interesting associations.

## Key Python Packages

- `pandas` for data manipulation
- `mlxtend.frequent_patterns` for Apriori and association rules

## Example Output

![Top Rules Screenshot](images/top_rules_screenshot.png)

Let's take this example:

| antecedents | consequents | confidence | lift | leverage | conviction |
|-------------|-------------|------------|------|----------|------------|
| rolls/buns  | whole milk  | 0.127      | 0.804 | -0.0034 | 0.964      |

- **Interpretation**:
  - Customers who buy `rolls/buns` also buy `whole milk` ~12.7% of the time.
  - The **lift** of **0.80** means this combo is **less likely than chance** (not a strong association).
  - **Leverage** is negative: the actual co-occurrence is slightly **less than expected**.
  - **Conviction** < 1: suggests **weak implication**.

## Requirements

```bash
pip install pandas mlxtend
```

---

## 📌 Credits

* Dataset: [Groceries Dataset on Kaggle](https://www.kaggle.com/datasets/heeraldedhia/groceries-dataset/data)
* Author: *Dean*