# E-commerce Customer Segmentation

## Project Overview
This project focuses on segmenting e-commerce customers based on their transactional behavior and demographic information. Using **unsupervised learning techniques**, we aim to identify distinct customer groups to help optimize coupon distribution strategies for increased customer loyalty and satisfaction.

## Dataset Description
The dataset consists of multiple interrelated tables that provide a comprehensive view of customer transactions and behaviors:
Customers Table: Contains customer demographics, including gender and city information.
Genders Table: Maps gender_id to gender labels (e.g., Male, Female).
Cities Table: Maps city_id to city names.
Transactions Table: Tracks coupon transactions, including transaction date, transactions status (subscribed or burned), and burn date and etc.
Branches Table: Links branch IDs to merchant IDs.
Merchants Table: Maps merchant IDs to merchant names.

## Methodology
1. **Data Preprocessing**
   - Merged multiple tables to create a unified dataset.
   - Converted merged tables into a customer-based table for clustering analysis.
   - Handled categorical colmons.
   - Removed unnecessary columns to reduce dimensionality.
   - Handled missing values
   - Checked duplicated rows to handle them.
   - Handled outliers using statistical techniques (IQR, log transformation).
   - Applied scaling, log transformation, and standardization for numerical stability.
       
2. **Feature Engineering**
   - Calculated customer tenure, preferred transaction month, preferred burn month, burned ratio, and days since last burn.
   - Identified preferred branches and merchants based on transaction frequency.
   - Extracted most common transaction and burn patterns by analyzing historical trends.
   - Grouped transaction history by customer ID to create aggregated insights.

3. **Clustering Models**
   - **K-Means Clustering** (Used Elbow Method & Silhouette Score to determine K = 2 and K = 3).
   - **DBSCAN** (Tested but performed poorly).
   - **Hierarchical Clustering** (Dendrogram used for cluster validation).

4. **Evaluation Metrics**
   - **Silhouette Score**: Measures cluster separation.
   - **Davies-Bouldin Index**: Measures cluster compactness.

## 🔍 Key Findings (K = 2 vs. K = 3)
| Metric | K = 2 | K = 3 | Best Choice |
|--------|------|------|--------------|
| **Silhouette Score** | **0.2556** | 0.1420 | **K = 2** (better separation) |
| **DB Index** | **1.27** | 2.08 | **K = 2** (more compact clusters) |
| **PCA Visualization** | **Two distinct groups** | Overlapping clusters | **K = 2** |
| **Dendrogram** | Two clear segments | Three subgroups | **K = 2** |

- **K = 2 is the best choice** for segmentation.
- **K = 3 provides more granularity**, but clusters overlap.
- **DBSCAN failed to form meaningful clusters** due to high-dimensional noise.

## 🎯 Business Recommendations
- **Cluster 0 (High Engagement):** Frequent coupon users → Offer loyalty rewards.
- **Cluster 1 (Low Engagement):** Inactive users → Send targeted promotions & re-engagement offers.
- K = 2 is recommended for a simpler and more interpretable segmentation strategy, ensuring distinct and well-separated customer groups. It allows for more effective targeting of high-value customers while identifying those needing engagement efforts.
- K = 3, while overlapping, provides a more detailed breakdown of customer behaviors, which may be useful for fine-tuned marketing strategies or personalized incentives.

---

## **Installation & Usage**
### **Clone this repository**
```bash
git clone https://github.com/asaazamaan/E_commerce_Customers_Segmentation.git
cd E_commerce_Customers_Segmentation
```

---
## **Acknowledgments**
✔️ **Developed as part of the MLSC Data Science & Machine Learning Course Graduation Project**  
---

