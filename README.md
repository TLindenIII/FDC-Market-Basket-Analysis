# 🛒 FDC Market Basket Analysis

This project performs **Market Basket Analysis** on customer delivery data using the **Apriori algorithm** from `mlxtend`.  
It identifies frequent itemsets and generates association rules between SKUs to uncover purchasing patterns.

---

## 📂 Project Overview

**Goal:**  
Analyze transaction-level data from customer deliveries to discover item associations — e.g., *"Customers who ordered SKU A often also ordered SKU B."*

**Tech Stack:**
- 🐍 Python  
- 📊 pandas  
- ⚙️ mlxtend (`apriori`, `association_rules`)  
- 📈 Jupyter / Kaggle Notebook

---

## 📑 Workflow Summary

1. **Data Import**
   - Read the Excel file `FDC_Customer_Deliveries.xlsx`  
   - Sheet name: `FDC_Customer_Deliveries`

2. **Basket Creation**
   - Group by `HDW Order Number` and `SKU Nbr`
   - Pivot to a one-hot encoded table of SKUs per order

3. **Frequent Itemset Mining**
   - Run the Apriori algorithm with `min_support = 0.01`
   - Output: list of item combinations that frequently occur together

4. **Association Rule Generation**
   - Use `association_rules()` with metric = `"lift"`
   - Key metrics:
     - **Support:** proportion of orders containing the itemset  
     - **Confidence:** likelihood that SKU B is bought when SKU A is bought  
     - **Lift:** how much more likely A and B are bought together vs. at random  

5. **Export Results**
   - Save the resulting DataFrames to:
     - `association_rules.csv` (raw rules)
     - `final_association_rules.csv` (cleaned and formatted)

6. **Optional Visualization**
   - Heatmap of top co-occurring SKUs (not shown here but easy to extend)

---

## 📊 Example Output

| support | confidence | lift | SKU1 | SKU2 |
|:--------|:-----------|:-----|:-----|:-----|
| 0.12 | 0.65 | 1.8 | 12345 | 67890 |
| 0.08 | 0.72 | 2.1 | 45678 | 98765 |

---

## 🧠 Interpretation

- **Lift > 1:** Positive correlation — items are bought together more than expected.
- **Lift = 1:** No correlation — random co-occurrence.
- **Lift < 1:** Negative correlation — items rarely appear together.

These insights can guide **cross-selling strategies**, **store layout optimization**, and **promotion bundling**.

---
