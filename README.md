# network-behavior-analysis-ml
Behavioral analysis of network traffic using machine learning to detect and classify cyber threats. Built on CIC-IDS2017 data with PCA + XGBoost.

# 🚨 Behavioral Analysis of Network Traffic using Machine Learning

This project detects and classifies network anomalies using supervised machine learning on labeled traffic data (from the CIC-IDS2017 dataset). It performs data cleaning, exploratory data analysis, feature selection, dimensionality reduction using PCA, and trains multiple classification models to identify cyberattacks.

---

## 📁 Dataset Details

- **Source**: CIC-IDS2017
- **Format**: 8 `.parquet` files (split by weekday)
- **Target Variable**: `Label` with 15 classes (Benign, DDoS, DoS Hulk, etc.)
- **Features**: 80+ including:
  - Flow metrics (`Flow Duration`, `Flow Bytes/s`)
  - Packet stats (`Packet Length Std`, `Fwd Packet Length Mean`)
  - Protocols and flags (`Protocol`, `SYN Flag Count`, etc.)

---

## 🔍 Project Steps

### 1. Data Preparation
- Loaded all `.parquet` files and concatenated them
- Verified and standardized column structure
- Dropped columns with missing values

### 2. Exploratory Data Analysis (EDA)
- Label distribution visualization
- Feature histograms and protocol heatmaps
- PCA/t-SNE plots for clustering view

### 3. Feature Engineering
- Label encoding
- Correlation analysis (PointBiserial)
- PCA for dimensionality reduction (95% variance retained)

### 4. Model Training & Evaluation

| Model              | Accuracy | F1 Macro |
|-------------------|----------|----------|
| ✅ XGBoost         | 99.80%   | 0.83     |
| Random Forest      | 99.81%   | 0.82     |
| Logistic Regression| 97.14%   | 0.41     |
| LightGBM           | 93.76%   | 0.30     |

- Evaluation metrics: Accuracy, F1-Macro, Classification Report

---

## 🧠 Best Model: XGBoost

- Robust performance across rare & common attacks
- Saved as `xgboost_best_model.pkl`

### Usage:

```python
import pickle
with open("xgboost_best_model.pkl", "rb") as f:
    model = pickle.load(f)

y_pred = model.predict(X_test)
```

---

## 📂 Project Structure

```
📦 network-traffic-ml/
├── Network_Behavior_Analysis.ipynb     ← Main notebook
├── xgboost_best_model.pkl              ← Trained model
├── requirements.txt                    ← Python dependencies
└── README.md                           ← Project overview
```

---

## 🚀 How to Run

1. Clone the repo
2. Install dependencies:
```bash
pip install -r requirements.txt
```
3. Launch Jupyter:
```bash
jupyter notebook Network_Behavior_Analysis.ipynb
```

---

## ✨ Highlights

- ✅ Real-world dataset
- ✅ 15-class classification
- ✅ PCA + ML modeling
- ✅ GitHub-optimized format

---

## 👨‍💻 Author

**Adity [Your Name Here]**  
_Data Analyst Intern – Cybersecurity_  
LinkedIn: [YourProfile]  
GitHub: [YourGitHub]

---

## 🛡️ License

This project is licensed under the MIT License.
