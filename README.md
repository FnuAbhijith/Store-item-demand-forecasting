# Store Item Demand Forecasting (End-to-End) 📈

This repository contains an **end-to-end demand forecasting project** for multiple stores and items.
It includes exploratory analysis, feature engineering, model training, evaluation, and **deployment to AWS** (artifact included).

## Contents
- `notebooks/Store_Item_Demand_Forecast.ipynb` — main notebook: EDA → features → models → evaluation
- `artifacts/model.tar.gz` — trained model artifact (e.g., for AWS deployment)
- `scripts/` — helper scripts (local inference, deployment template)
- `requirements.txt` — Python dependencies
- `data/` — put raw CSVs here (ignored by Git)

## Quickstart
```bash
# 1) Create & activate environment (optional)
conda create -n store-forecast python=3.11 -y
conda activate store-forecast

# 2) Install dependencies
pip install -r requirements.txt

# 3) Explore / run the notebook
jupyter notebook notebooks/Store_Item_Demand_Forecast.ipynb
```

## Local Inference (example)
```bash
python scripts/local_infer.py --model artifacts/model.tar.gz --csv data/sample_input.csv
```

> Update the script to match your model’s expected inputs/outputs if needed.

## AWS Deployment (Template)
If you deployed on **AWS** (e.g., SageMaker/EC2), this repo packages the **trained artifact** at `artifacts/model.tar.gz`.
- For **SageMaker**, upload the artifact to S3 and point a Model/Endpoint to it.
- For **EC2**, unpack and run your inference server (FastAPI/Flask) loading the model.

See `scripts/deploy_sagemaker_template.py` for a minimal template you can adapt.

## Data layout
Place your data in `./data/` (ignored by Git):
```
data/
  ├── train.csv
  ├── test.csv
  └── items.csv        # optional
```

## Typical Features & Models
- Time features: lags, rolling means, moving averages, day/week/month, holiday flags
- Models: Linear/ElasticNet/Ridge, RandomForest, XGBoost/LightGBM, or classical TS (ARIMA/Prophet)
- Evaluation: RMSE/MAE + backtesting (sliding window)

## Notes
- Large files are ignored via `.gitignore` (except `artifacts/model.tar.gz`, which is included here as requested).
- Adjust `requirements.txt` to match your environment if necessary.

## Author
**Abhijith Shetty** — Data Science
