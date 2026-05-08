# ChurnGuard: Telecom Customer Churn Analysis

> End-to-end exploratory data analysis project on telecom customer churn using Python — covering data cleaning, preprocessing, feature engineering, scaling, and visualization to uncover key churn-driving factors.

---

## Project Overview

Customer churn is one of the biggest challenges in the telecom industry. This project analyses a telecom customer dataset to identify patterns and factors that drive churn. The entire pipeline — from raw data to insights — is built in Python using a Jupyter Notebook.

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| Python | Core language |
| Pandas & NumPy | Data manipulation and analysis |
| Matplotlib & Seaborn | Data visualization |
| Scikit-learn | Label encoding and feature scaling |
| Jupyter Notebook | Development environment |

---

## Dataset

- **File:** `Churn_dataset.csv`
- **Source:** Telecom customer dataset (Kaggle / UCI)
- **Key columns:** `account length`, `international plan`, `voice mail plan`, `total day/eve/night/intl calls`, `total day/eve/night/intl charge`, `customer service calls`, `churn`

---

## Project Structure

```
ChurnGuard/
│
├── PROJECT_1-Telecom_churn_analysis.ipynb   # Main analysis notebook
├── Churn_dataset.csv                         # Dataset (download separately)
└── README.md
```

---

## Workflow

### 1. Data Exploration
- Loaded dataset and inspected shape, dtypes, and descriptive statistics
- Checked dimensions, size, and value distributions using `df.info()`, `df.describe()`, `df.shape`

### 2. Data Cleaning
- Checked and confirmed zero duplicate rows
- Identified null values in call-related columns (`total day calls`, `total eve calls`, `total night calls`, `total intl calls`)
- Plotted histograms to check skewness of null columns
- Filled null values with **median** (appropriate for skewed distributions)

### 3. Data Preprocessing
- Identified categorical columns: `international plan`, `voice mail plan`, `churn`
- Applied **LabelEncoder** to convert categorical features to numerical values for analysis

### 4. Feature Engineering
Created 3 new aggregated features from existing columns:
- `total duration` = sum of day + eve + night + intl minutes
- `total calls` = sum of day + eve + night + intl calls
- `total charge` = sum of day + eve + night + intl charges

Dropped low-value columns:
- `phone number`, `area code` (not useful for churn analysis)
- Individual minute columns (replaced by `total duration`)

### 5. Feature Scaling
- Applied **MinMaxScaler** to all numerical columns
- Ensures all features are on the same scale so no single feature dominates analysis

### 6. Churn Factor Analysis
Grouped data by churn to analyse mean values of key features:
- **Customer service calls** — churned customers had significantly higher average calls
- **Total charge** — churned customers had higher average total charges
- **International plan** — higher proportion of churned customers had international plans
- **Voice mail plan** — lower voice mail plan adoption among churned customers

### 7. Visualizations
- **Correlation heatmap** — identifies relationships between all numerical features
- **Line chart** — customer service call frequency distribution
- **Pie chart** — overall churn vs non-churn percentage distribution
- **Count plot** — churn distribution
- **Bar plots** — churn vs customer service calls, total charge, international plan, voice mail plan
- **Box plots** — churn vs customer service calls and total charge (outlier detection)
- **Histogram with KDE** — total charge frequency by churn status
- **Scatter plot** — total charge vs total duration coloured by churn

---

## Key Insights

- **Customer service calls** have the strongest relationship with churn — customers who call support frequently are far more likely to leave, indicating unresolved issues or poor service quality
- **International plan users** churn at a higher rate — possibly due to expensive international rates or dissatisfaction with coverage
- **Higher total charges** are associated with increased churn — high billing amounts reduce customer satisfaction and push customers toward competitors
- The majority of customers do not churn, but the churned segment shows clear and consistent behavioural patterns across multiple features

---

## How to Run

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### Steps

1. **Clone the repo**
   ```bash
   git clone https://github.com/kirana-23/ChurnGuard.git
   cd ChurnGuard
   ```

2. **Download the dataset**
   - Download `Churn_dataset.csv` from Kaggle (Telecom Customer Churn dataset)
   - Place it in the project folder
   - Update the file path in the notebook:
     ```python
     df = pd.read_csv("Churn_dataset.csv")
     ```

3. **Launch Jupyter Notebook**
   ```bash
   jupyter notebook
   ```

4. **Open and run**
   - Open `PROJECT_1-Telecom_churn_analysis.ipynb`
   - Run all cells from top to bottom (`Kernel → Restart & Run All`)

---

## Author

**Kirana B**
- GitHub: [github.com/kirana-23](https://github.com/kirana-23)
- LinkedIn: [linkedin.com/in/kirana-kira23](https://www.linkedin.com/in/kirana-kira23)
- Email: kirana232004@gmail.com
