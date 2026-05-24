# 🫀 Heart Disease Prediction — CodeAlpha Internship Task 4

> **Predict the possibility of heart disease** based on patient clinical data using multiple ML classification algorithms with a full-stack web interface.

---

## 📌 Project Overview

This project was developed as **Task 4** of the [CodeAlpha](https://www.codealpha.tech/) Machine Learning Internship. It applies supervised classification techniques to structured medical data to predict whether a patient is at risk of heart disease.

The system features a complete ML training pipeline on the back end and a modern React-based UI on the front end, connected via a REST API.

---

## ✨ Features

- 🧠 Trains and compares **5 ML models** with hyperparameter tuning via GridSearchCV
- ⚖️ Handles class imbalance using **SMOTE** oversampling
- 🔧 Includes **feature engineering** (interaction terms, polynomial features)
- 📊 Evaluates models with Accuracy, Precision, Recall, F1-Score, and ROC-AUC
- 🌐 REST API built with **Flask** for real-time predictions
- 💻 Interactive **React + Vite** frontend with animated UI
- 📦 Persists trained model artifacts (`.pkl` files) for fast inference

---

## 🗂️ Project Structure

```
HeartMLProject/
├── backend/
│   ├── app.py                  # Flask REST API
│   ├── train_model.py          # ML training pipeline
│   ├── requirements.txt        # Python dependencies
│   ├── data/
│   │   └── heart.csv           # UCI Heart Disease dataset
│   ├── models/
│   │   ├── trained_model.pkl   # Best trained model
│   │   ├── scaler.pkl          # StandardScaler
│   │   ├── columns.pkl         # Feature column order
│   │   └── metadata.pkl        # Model performance metadata
│   └── utils/
│       ├── preprocess.py       # Feature engineering & preprocessing
│       └── __init__.py
├── frontend/
│   ├── src/
│   │   ├── App.jsx             # Main React application
│   │   ├── services/api.js     # Axios API service
│   │   ├── main.jsx
│   │   └── index.css
│   ├── public/
│   ├── package.json
│   └── vite.config.js
└── README.md
```

---

## 🧬 Dataset

**Source:** [UCI ML Repository — Heart Failure Prediction Dataset](https://archive.ics.uci.edu/ml/datasets/Heart+Disease)

| Feature | Description |
|---|---|
| `Age` | Patient age (years) |
| `Sex` | M = Male, F = Female |
| `ChestPainType` | TA / ATA / NAP / ASY |
| `RestingBP` | Resting blood pressure (mm Hg) |
| `Cholesterol` | Serum cholesterol (mg/dL) |
| `FastingBS` | Fasting blood sugar > 120 mg/dL (1 = true) |
| `RestingECG` | Resting ECG results (Normal / ST / LVH) |
| `MaxHR` | Maximum heart rate achieved |
| `ExerciseAngina` | Exercise-induced angina (Y / N) |
| `Oldpeak` | ST depression induced by exercise |
| `ST_Slope` | Slope of peak exercise ST segment |
| `HeartDisease` | **Target** — 1 = disease, 0 = normal |

---

## 🤖 ML Pipeline

### Algorithms Used
- Logistic Regression
- Random Forest
- XGBoost
- Gradient Boosting
- Support Vector Machine (SVM)

### Pipeline Steps
1. **Load dataset** from CSV (or generate synthetic if missing)
2. **Outlier removal** via IQR method on numeric columns
3. **Preprocessing & Feature Engineering** — one-hot encoding, interaction terms (`Age_HR`, `HR_BP_Ratio`, `Oldpeak_Slope`, `Age_Squared`)
4. **Train/Test split** (80/20, stratified)
5. **Standard scaling** with `StandardScaler`
6. **SMOTE** oversampling to address class imbalance
7. **GridSearchCV** with 5-fold Stratified Cross-Validation for each model
8. **Best model selection** by ROC-AUC score
9. **Save artifacts** — model, scaler, feature columns, metadata

---

## 🚀 Getting Started

### Prerequisites
- Python 3.9+
- Node.js 18+

---

### Backend Setup

```bash
# Navigate to backend
cd backend

# Install dependencies
pip install -r requirements.txt

# Train the model (generates trained_model.pkl and other artifacts)
python train_model.py

# Start the Flask API
python app.py
```

The API will be available at `http://localhost:5000`.

---

### Frontend Setup

```bash
# Navigate to frontend
cd frontend

# Install dependencies
npm install

# Start the development server
npm run dev
```

The UI will be available at `http://localhost:5173`.

---

## 🔌 API Endpoints

### `POST /predict`
Predicts heart disease risk from patient data.

**Request Body:**
```json
{
  "age": 52,
  "sex": "M",
  "chestPainType": "ASY",
  "restingBP": 125,
  "cholesterol": 212,
  "fastingBS": 0,
  "restingECG": "Normal",
  "maxHR": 168,
  "exerciseAngina": "N",
  "oldpeak": 1.0,
  "stSlope": "Up"
}
```

**Response:**
```json
{
  "prediction": "HIGH RISK",
  "probability": 74.3,
  "confidence": 74.3,
  "details": {
    "heart_disease_prob": 74.3,
    "healthy_prob": 25.7
  }
}
```

### `GET /model-info`
Returns the current model's performance metrics (accuracy, ROC-AUC, F1, etc.).

### `GET /health`
Health check endpoint — returns API and model load status.

---

## 🧪 Model Evaluation Metrics

| Metric | Description |
|---|---|
| **Accuracy** | Overall correct predictions |
| **Precision** | True positives among predicted positives |
| **Recall** | True positives among actual positives |
| **F1-Score** | Harmonic mean of precision and recall |
| **ROC-AUC** | Area under the ROC curve (primary selection metric) |

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| ML / Data | Python, scikit-learn, XGBoost, imbalanced-learn, pandas, NumPy |
| API | Flask, Flask-CORS |
| Frontend | React 19, Vite, Tailwind CSS, Framer Motion, Axios |
| Serialization | joblib |

---

## 📸 Screenshots

> UI built with React + Tailwind CSS featuring an animated ECG line, toggle chip inputs, and real-time risk prediction display.

---

## 🙏 Acknowledgements

- [CodeAlpha](https://www.codealpha.tech/) for the internship opportunity
- [UCI Machine Learning Repository](https://archive.ics.uci.edu/) for the Heart Disease dataset
- scikit-learn, XGBoost, and the open-source ML community

---

## 👤 Author

**Khilan Kaneriya**
Machine Learning Intern — CodeAlpha
[GitHub](https://github.com/khilan023) · [LinkedIn](https://linkedin.com/in/yourprofile)

---

> ⚠️ **Disclaimer:** This project is built for educational purposes only. It is not intended for clinical or medical diagnosis. Always consult a qualified healthcare professional for medical advice.
