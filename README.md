# 🎗️ Cancer Risk Prediction — ML Web App

> A machine learning web application that predicts an individual's cancer risk level (**Low / Medium / High**) based on demographic, lifestyle, and genetic health features.

---


## 📌 Project Overview

Cancer risk prediction is a critical challenge in healthcare. Early identification of high-risk individuals can lead to timely interventions and better health outcomes.

This project uses a combination of **demographic**, **lifestyle**, **environmental**, and **genetic** features to classify patients into three risk categories. The model was trained on a real-world inspired dataset and went through multiple experiments to handle **class imbalance** — ensuring the minority (High risk) class is predicted with strong recall.

**Final Model:** Optuna-Tuned Class-Weighted XGBoost  
**Overall Accuracy:** 88% | **Macro F1:** 0.72 | **High-Risk Recall:** 0.45

---

## 📂 Dataset Description

The dataset contains patient records with the following feature groups:

| Category | Features |
|---|---|
| **Demographics** | Age, Gender (0=Female, 1=Male), BMI |
| **Lifestyle & Environmental** (0–10 index) | Smoking, Alcohol Use, Obesity, Diet Red Meat, Diet Salted/Processed, Fruit & Veg Intake, Physical Activity, Air Pollution, Occupational Hazards, Calcium Intake |
| **Genetic / Medical Flags** (0 or 1) | Family History, BRCA Mutation, H. Pylori Infection |
| **Target** | Risk Level (Low / Medium / High) |

**Key Data Notes:**
- Prostate cancer occurs only when Gender = 1 (Male)
- Risk Level is moderately imbalanced — Medium is the majority class
- The composite risk score aligns directionally with exposure intensity

---

## 🔍 EDA Highlights

- **Class Imbalance:** Medium risk is the dominant class (~1,580 patients), followed by Low (~330) and High (~110)
- **Top Risk Factors for High Risk:** Air Pollution, Smoking, Alcohol Use, Diet (Salted/Processed & Red Meat), Occupational Hazards, Obesity
- **BMI:** Surprisingly, BMI alone does not strongly determine risk level
- **Young Patients (<30 yrs):** Only 3 patients under 30 — all females with lung cancer
- **Gender & Cancer Type:** Females most affected by Breast cancer (455 cases); Males most affected by Prostate cancer (305 cases)

---

## 🧪 Model Performance

Multiple models and strategies were evaluated to handle class imbalance:

| Model | Accuracy | Macro F1 | Weighted F1 | High Recall | Low Recall | Medium Recall |
|---|---|---|---|---|---|---|
| Random Forest (Baseline) | 0.84 | 0.64 | 0.83 | 0.35 | 0.58 | 0.92 |
| Optuna-Tuned RF (Macro F1) | 0.83 | 0.65 | 0.83 | 0.45 | 0.63 | 0.89 |
| Optuna-Tuned RF (High Recall) | 0.80 | 0.65 | 0.81 | 0.60 | 0.74 | 0.82 |
| XGBoost + SMOTE | 0.85 | 0.68 | 0.85 | 0.45 | 0.68 | 0.92 |
| Class-Weighted XGBoost | 0.64 | 0.54 | 0.67 | 0.75 | 0.82 | 0.59 |
| **✅ Optuna + Class-Weighted XGBoost** | **0.88** | **0.72** | **0.87** | **0.45** | **0.78** | **0.92** |

**Final Model selected:** Optuna-Tuned Class-Weighted XGBoost — best overall balance between accuracy and minority class recall.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core language |
| XGBoost | Final ML model |
| Scikit-learn | Preprocessing, evaluation |
| SMOTE (imbalanced-learn) | Class balancing |
| Optuna | Hyperparameter tuning |
| Streamlit | Web application |
| Pandas / NumPy | Data manipulation |
| Matplotlib / Seaborn | EDA visualizations |

---

## 🚀 How to Run Locally

**1. Clone the repository**
```bash
git clone https://github.com/kedareak/Cancer-Risk-Prediction.git
cd Cancer-Risk-Prediction
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Run the Streamlit app**
```bash
streamlit run app.py
```

**4. Open in browser**
```
http://localhost:8501
```

---

## 📁 Project Structure

```
Cancer-Risk-Prediction/
│
├── app.py                          # Streamlit web application
├── main.py                         # Entry point
├── Cancer_Risk_Prediction_(ML).ipynb  # Full ML notebook (EDA + Training)
├── cancer-risk-factors.xls         # Dataset
├── final_xgb_class_weighted.pkl    # Trained XGBoost model
├── feature_names.pkl               # Feature names used during training
├── label_encoder.pkl               # Label encoder for target variable
├── requirements.txt                # Python dependencies
├── pyproject.toml                  # Project config
└── README.md                       # Project documentation
```

---

## 🌐 Live Demo

> _Deploy on Streamlit Cloud and add the link here!_  
> After pushing to GitHub → go to [share.streamlit.io](https://share.streamlit.io) → connect your repo → deploy → paste the link here.

---

## 👤 Author

**Akshay Kedare**  
📧 akshaykedare34@gmail.com  
🔗 [GitHub](https://github.com/kedareak)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
