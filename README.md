# SAP Customer Clustering Analysis

This project analyzes SAP sales transaction data to segment customers using **RFM analysis** and **K-Means clustering**.

The objective is to identify distinct customer groups based on purchasing behavior and support business decisions related to customer retention, targeting, and value analysis.

## Project Overview

The dataset contains invoice-level transaction data extracted from SAP, including customer IDs, invoice dates, invoice numbers, and net sales values.

The project converts this transaction data into customer-level **Recency, Frequency, and Monetary (RFM)** metrics and then applies K-Means clustering to identify groups of customers with similar purchasing behavior.

## Business Objective

The goal is to better understand customer behavior and identify customer segments such as:

- High-value loyal customers
- Frequent but lower-value customers
- Recent customers with low spend
- Inactive or churn-risk customers

These insights can support:

- Customer retention strategies
- Marketing targeting
- Sales prioritization
- Customer value analysis

## SAP Data Extraction

The sales transaction data used in this project was extracted from the **SAP system** before being analyzed in Python.

Using the SAP interface, relevant billing and invoice information was retrieved from SAP billing data, including information from:

- **VBRK** – Billing Document Header Data
- **VBRP** – Billing Document Item Data

The required fields were selected from the SAP data and exported to Excel for further analysis.

This created an end-to-end workflow:

**SAP → Excel → Python → RFM Analysis → K-Means Clustering → Customer Segments**

This process provided practical experience working with the SAP interface, identifying relevant business data, extracting transaction records, and preparing SAP data for analytical use.

## Dataset

The extracted SAP invoice data is stored in:

`Invoice Data 1.xlsx`

The analysis uses invoice-level information such as:

| Field | Description |
|---|---|
| `CustomerID` | Unique customer identifier |
| `InvoiceNo` | Invoice or billing document number |
| `InvoiceDate` | Date of the transaction |
| `NetValue` | Net monetary value of the transaction |

## Methodology

The project follows an RFM-based customer segmentation workflow:

1. Load and clean the SAP transaction data
2. Convert invoice dates into datetime format
3. Aggregate invoice data at the customer level
4. Calculate RFM metrics:
   - **Recency** – Days since the customer's most recent purchase
   - **Frequency** – Number of purchases made by the customer
   - **Monetary Value** – Total amount spent by the customer
5. Apply log transformation to reduce skewness
6. Standardize the RFM features
7. Use the **Elbow Method** and **Silhouette Score** to evaluate the number of clusters
8. Apply **K-Means clustering**
9. Analyze the characteristics of each customer cluster
10. Visualize and interpret the resulting customer segments

## Tools and Libraries

- SAP
- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- OpenPyXL
- Jupyter Notebook

## Project Structure

```text
SAP-Customer-Clustering/
│
├── Clustering on SAP Data Final.ipynb
├── Invoice Data 1.xlsx
└── README.md
```

## Setup Instructions

Clone or download the project and navigate to the project directory.

### 1. Create a virtual environment

```bash
python -m venv .venv
```

### 2. Activate the virtual environment

On Windows:

```bash
.\.venv\Scripts\activate
```

### 3. Install the required libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl
```

If you are using **VS Code**, make sure the Jupyter notebook is using the same Python environment where the packages were installed.

Select the `.venv` Python interpreter as the notebook kernel before running the analysis.

## How to Run

Open:

`Clustering on SAP Data Final.ipynb`

Run all notebook cells in order.

The workflow includes:

- Loading the SAP invoice dataset
- Cleaning and preparing transaction data
- Creating customer-level RFM features
- Transforming and scaling the RFM data
- Identifying the optimal number of clusters
- Applying K-Means clustering
- Analyzing customer groups
- Visualizing customer segments

## Outputs

The notebook generates:

- **Customer RFM Summary** – Recency, Frequency, and Monetary Value for each customer
- **Distribution Plots** – Visualizations of the RFM feature distributions
- **Elbow Method Chart** – Comparison of cluster inertia across different values of K
- **Silhouette Analysis** – Evaluation of cluster separation and quality
- **Cluster Summary Statistics** – Comparison of average RFM characteristics across clusters
- **3D Customer Cluster Visualization** – Visualization of customers across Recency, Frequency, and Monetary dimensions

## Business Interpretation

The resulting clusters can be analyzed based on their RFM characteristics to identify different types of customers.

| Customer Segment | Typical Behaviour | Possible Business Action |
|---|---|---|
| High-Value Loyal | Frequent, recent and high-spending | Retain and reward |
| Frequent Lower-Value | Purchases often but spends less | Cross-sell or upsell |
| Recent Low-Spend | Purchased recently but has limited spending history | Encourage repeat purchases |
| Inactive / Churn Risk | Long time since last purchase | Re-engagement campaigns |

The actual segment labels should be assigned after examining the RFM characteristics of the clusters produced by the model.

## Final Notes

This project demonstrates a practical approach to customer segmentation using SAP sales transaction data.

It covers the workflow from **SAP data extraction and preparation to customer-level analytics and machine learning**.

The analysis can be extended further with:

- Product-level purchasing behavior
- Customer profitability analysis
- Churn prediction
- Customer lifetime value
- Geographic or sales-region segmentation
- Marketing campaign targeting
- Interactive Power BI or Tableau dashboards
