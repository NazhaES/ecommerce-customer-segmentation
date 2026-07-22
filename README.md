# Customer Segmentation using RFM Analysis & K-Means Clustering

Segments customers of a UK-based online retailer into actionable groups using RFM (Recency, Frequency, Monetary) analysis and K-Means clustering, applied to 1M+ real transaction records.

## 📊 Overview

Raw transaction data doesn't tell you who your best customers are, who's about to churn, or who deserves VIP treatment. This project builds an end-to-end pipeline that turns messy e-commerce transaction logs into 7 clear, labeled customer segments — each with a data-backed rationale and a recommended business action.


## Pipeline

1. **Data Cleaning** — removed invalid invoice numbers, invalid stock/product codes, missing Customer IDs, and zero/negative prices (~23% of rows dropped as noise)
2. **Feature Engineering (RFM)** — aggregated cleaned transactions into per-customer Recency, Frequency, and Monetary Value
3. **Outlier Detection** — used the IQR method on Monetary Value and Frequency to isolate statistical outliers before clustering
4. **Scaling** — standardized RFM features with `StandardScaler`
5. **Cluster Selection** — evaluated k = 2–12 using the elbow method (inertia) and silhouette scores
6. **Clustering** — applied K-Means (k=4) to the core (non-outlier) customer base
7. **Segment Labeling** — profiled each cluster's RFM distributions and translated them into business-friendly segments

## Results — 7 Customer Segments

**Core segments (K-Means):**

| Segment | Profile | Recommended Action |
|---|---|---|
| Retain | High-value, regular buyers, not always recent | Loyalty programs, personalized offers |
| Re-Engage | Lower value, inactive, haven't bought recently | Targeted win-back campaigns |
| Nurture | Low activity, but recent buyers | Relationship-building, incentives |
| Reward | High-value, frequent, still active | VIP loyalty program |

**Outlier segments (IQR-based, handled separately):**

| Segment | Profile | Recommended Action |
|---|---|---|
| Pamper | High spend, infrequent | Personalized luxury offers |
| Upsell | Frequent, lower spend per order | Bundles / loyalty deals |
| Delight | Extreme spend + frequency (top-tier) | Dedicated VIP program |

## Visualizations

- 3D scatter plot of customers by Monetary Value / Frequency / Recency, colored by segment
- Cluster distribution with average RFM values per segment
- Elbow & silhouette score plots (cluster selection justification)
- Violin plots of RFM distributions per cluster

## Tech Stack

- **Language:** Python
- **Data processing:** pandas
- **Machine Learning:** scikit-learn (`KMeans`, `StandardScaler`, `silhouette_score`)
- **Visualization:** matplotlib, seaborn










## 📄 License

This project is open source and available under the [MIT License](LICENSE).
