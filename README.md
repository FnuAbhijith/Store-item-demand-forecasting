# 🛍️ Store Item Demand Forecasting (End-to-End with AWS Deployment)  

This repository contains an **end-to-end machine learning pipeline** for **store-item demand forecasting**.  
It covers **data preparation, feature engineering, model training, evaluation, and deployment on AWS** (artifact included).  

---

## 📌 Project Overview  
- **Data Exploration & Feature Engineering:** Time-based lags, rolling averages, seasonality, holiday flags.  
- **Model Training:** Classical ML (XGBoost, LightGBM, RandomForest) & statistical methods.  
- **Evaluation:** RMSE / MAE with backtesting via sliding windows.  
- **Deployment:** Packaged model (`artifacts/model.tar.gz`) for AWS SageMaker / EC2 deployment.  

---

## 📂 Repository Structure  
```
├── notebooks/
│   └── Store_Item_Demand_Forecast.ipynb    # Main notebook (EDA → Features → Modeling → Evaluation)
├── artifacts/
│   └── model.tar.gz                        # Trained model artifact (ready for AWS deployment)
├── scripts/
│   ├── local_infer.py                      # Local inference helper (load artifact, test predictions)
│   └── deploy_sagemaker_template.py        # Minimal SageMaker deployment template
├── data/
│   └── .gitkeep                            # Placeholder (datasets ignored in Git)
├── requirements.txt                        # Dependencies
├── .gitignore                              # Ignore unnecessary files & large data
└── README.md                               # Documentation
```

---

## ⚙️ Setup & Installation  
1. Clone the repository:  
```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```

2. Create & activate environment:  
```bash
conda create -n store-forecast python=3.11 -y
conda activate store-forecast
```

3. Install dependencies:  
```bash
pip install -r requirements.txt
```

4. Run the notebook:  
```bash
jupyter notebook notebooks/Store_Item_Demand_Forecast.ipynb
```

---

## 📊 Datasets  
Expected layout in `data/` (ignored in GitHub):  
```
data/
  ├── train.csv
  ├── test.csv
  └── items.csv
```

---

## 🚀 AWS Deployment  

### ✅ Using SageMaker  
- Upload `artifacts/model.tar.gz` to S3  
- Use `scripts/deploy_sagemaker_template.py` to create SageMaker Model & Endpoint  
- Endpoint serves real-time predictions  

### ✅ Using EC2  
- Copy `model.tar.gz` to EC2 instance  
- Unpack & serve with **Flask/FastAPI** inference script  

---

## 📈 Results  
- Models benchmarked: XGBoost, LightGBM, RandomForest, Linear Regression  
- Evaluation: RMSE & MAE across backtesting windows  
- Insights: seasonality & store-level variation captured by engineered features  

---

## 🔑 Key Highlights  
- **Time-series demand forecasting** with engineered features  
- **Multiple models tested** with evaluation metrics  
- **Deployment-ready artifact** for AWS SageMaker/EC2  
- **End-to-end pipeline**: data → model → evaluation → deployment  

---

## 👤 Author  
**Abhijith Shetty**  
🎓 Master’s Student in Data Science, University of Memphis  
💼 Aspiring Data Scientist / ML Engineer  
🔗 [LinkedIn](https://www.linkedin.com/in/fnuabhijith) | [GitHub](https://github.com/FnuAbhijith) | [Portfolio](https://fnuabhijith.github.io/Abhijith-Portfolio)  

---

✨ *This project showcases applied forecasting, ML model building, and deployment — a complete workflow relevant for Data Scientist / ML Engineer roles.*  
