# 🛒 Retail Portfolio Optimization: SKU Segmentation with Machine Learning (Vanish)

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data_Manipulation-150458.svg)
![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Machine_Learning-F7931E.svg)
![Seaborn](https://img.shields.io/badge/Seaborn-Data_Visualization-44B78B.svg)

## 📝 Project Overview
This Data Science project applied to the Retail / FMCG (Fast-Moving Consumer Goods) sector aims to optimize the product portfolio of the **Vanish** brand. Through unsupervised machine learning techniques, the analysis transforms a massive transactional database (122k+ records) into a strategic profitability matrix.

The model identifies which products are the true financial drivers of the brand and detects "Dead Weights" (zombie SKUs) that generate unnecessary costs in the supply chain, enabling a data-driven SKU Rationalization strategy.

## 🚀 Data Pipeline and Methodology

1. **Data Engineering (Star Schema Consolidation):**
   - Structured fusion (`pd.merge`) of Fact tables (Sales) and Dimension tables (Product Catalog, Segment Rules, and Calendar).
   - Granularity shift: Aggregation of transactional data to generate SKU-level metrics: *Total Revenue, Total Units Sold, Sales Frequency, and Average Price*.
2. **Mathematical Preprocessing:**
   - Application of **Logarithmic Transformations (`np.log1p`)** to tame highly skewed distributions and handle outlier products ("Whales").
   - Feature standardization using `StandardScaler` to balance the mathematical weight of financial characteristics against frequency variables.
3. **Predictive Modeling (K-Means Clustering):**
   - Utilization of the **Elbow Method** to determine the existence of 4 optimal business clusters (k=4).
   - Training the K-Means algorithm to segment the brand's 77 distinct SKUs.

## 📊 Resulting Business Matrix
The algorithm achieved a perfect separation of the portfolio into 4 strategic quadrants (similar to the BCG Matrix):

* ⭐ **Stars / Heroes (30 SKUs):** The core of the brand. They generate the highest revenue volume with the highest frequency across all price ranges. *(Action: Protect inventory availability at all costs)*.
* 🐄 **Cash Cows (21 SKUs):** Medium-sized formats with solid volume and frequency, ideal for maintaining cash flow and regular pantry purchases. *(Action: Cross-selling promotions)*.
* ❓ **Question Marks (14 SKUs):** Products with good presence in shopping carts but marginal revenue (e.g., travel formats or sachets). *(Action: Review pricing strategy or Point-of-Sale display)*.
* 💀 **Dead Weights (12 SKUs):** The most critical finding. Codes with near-zero sales. Qualitative analysis demonstrated that **these are not product failures**, but rather "catalog clutter" (expired promotions, old 'Buy 2 Get 1' deals, and discontinued promotional kits). *(Action: Immediate delisting to save logistical and warehousing costs)*.

## 📈 Key Visualizations
The analysis includes a dashboard generated with Seaborn and Matplotlib using **logarithmic scales**, allowing for the visualization of the entire portfolio without data distortion. It includes:
- **Value Map:** Scatter plot of Revenue vs. Frequency by Segment.
- **Portfolio Elasticity:** Analysis of Units Sold vs. Average Price.
- **Financial Distribution:** Boxplots demonstrating the consistency of revenue per cluster.


