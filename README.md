# 🫀 CardioAI - Heart Disease Prediction Web Application

A premium AI-powered heart disease prediction system built with React, Flask, and Scikit-learn.

![CardioAI](https://img.shields.io/badge/CardioAI-Heart%20Disease%20Prediction-ff4d6d?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat-square)
![React](https://img.shields.io/badge/React-18-61dafb?style=flat-square)
![ML](https://img.shields.io/badge/ML-Scikit--Learn-orange?style=flat-square)

## ✨ Features

- **AI Prediction**: 90%+ ROC-AUC accuracy heart disease risk prediction
- **5 ML Models Compared**: Logistic Regression, Random Forest, XGBoost, Gradient Boosting, SVM
- **Premium Dark UI**: Glassmorphism, animations, ECG waveform, beating heart
- **Multi-Step Form**: Custom sliders, pill selectors, real-time validation
- **Risk Visualization**: Circular risk gauge, color-coded result cards
- **Health Tips**: Evidence-based cardiovascular health recommendations

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- Node.js 16+
- npm

### 1. Backend Setup

```bash
cd backend
pip install -r requirements.txt
python train_model.py     # Train the ML model
python app.py             # Start Flask API on port 5000
```

### 2. Frontend Setup

```bash
cd frontend
npm install
npm run dev               # Start Vite dev server on port 5173
```

### 3. Open the App
Navigate to `http://localhost:5173` in your browser.

## 📁 Project Structure

```
HeartMLProject/
├── backend/
│   ├── app.py                 # Flask REST API
│   ├── train_model.py         # ML training pipeline
│   ├── requirements.txt       # Python dependencies
│   ├── models/                # Saved model artifacts
│   │   ├── trained_model.pkl
│   │   ├── scaler.pkl
│   │   ├── columns.pkl
│   │   └── metadata.pkl
│   ├── data/
│   │   └── heart.csv          # Training dataset
│   └── utils/
│       └── preprocess.py      # Data preprocessing
├── frontend/
│   ├── src/
│   │   ├── components/        # React components
│   │   ├── animations/        # Framer Motion variants
│   │   ├── services/          # API service (Axios)
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   ├── index.html
│   └── package.json
└── README.md
```

## 🧠 ML Pipeline

1. **Data**: UCI Heart Disease dataset (918 samples, 11 features)
2. **Preprocessing**: Missing value handling, outlier removal, feature engineering
3. **SMOTE**: Handles class imbalance
4. **GridSearchCV**: Hyperparameter tuning for each model
5. **Cross-Validation**: 5-fold stratified CV
6. **Best Model Selection**: Automatically selects by ROC-AUC score

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/predict` | Predict heart disease risk |
| GET | `/model-info` | Get model metrics and info |
| GET | `/health` | Health check |

## 🎨 Tech Stack

**Frontend**: React 18, Vite, Tailwind CSS, Framer Motion, Axios, Lucide Icons
**Backend**: Flask, Flask-CORS, Scikit-learn, XGBoost, Pandas, NumPy, Joblib
**ML**: Logistic Regression, Random Forest, XGBoost, Gradient Boosting, SVM

## ⚠️ Disclaimer

This is an educational project and NOT a medical device. Always consult a qualified healthcare professional for medical advice.
