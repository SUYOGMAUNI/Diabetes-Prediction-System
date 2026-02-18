# 🩺 Diabetes Prediction System

A machine learning-based web application that predicts the likelihood of diabetes in patients based on health parameters including glucose level, BMI, blood pressure, insulin, and family history.

## 👤 Author

**Suyog Mauni**
[suyogmauni.com.np](https://suyogmauni.com.np) 

---

## 🌐 Live Demo

👉 [diabetes-prediction-system-vyuc.onrender.com](https://diabetes-prediction-system-vyuc.onrender.com/)

---

## 📌 Overview

Early detection of diabetes is crucial for effective disease management and prevention of complications. This system uses a **custom-built Random Forest Classifier** (built from scratch using NumPy — no sklearn RF) trained on the **Pima Indians Diabetes Dataset** to predict diabetes risk in real time.

The model achieved an accuracy of **86%**, with precision of **0.90**, recall of **0.88**, and F1 score of **0.88**.

---

## ✨ Features

- Real-time diabetes risk prediction via a web form
- **Custom Random Forest** built from scratch (Decision Tree + ensemble voting)
- Family history inputs auto-calculate the **Diabetes Pedigree Function (DPF)**
- BMI auto-calculated from height and weight inputs
- SMOTE applied for class balancing (500 samples per class)
- Data preprocessing with **median imputation** and **StandardScaler**
- Flask web backend with Jinja2 templates
- Deployed on Render

---

## 🧠 Model Architecture

The Random Forest is implemented entirely from scratch in `algo.py`:

- **DecisionTree** — grows using entropy + information gain, random feature subsets (√n features per split)
- **RandomForest** — ensemble of 30 decision trees, bootstrap sampling (80% of data per tree), majority voting for final prediction

### Performance Comparison

| Model | Accuracy | Precision | Recall | F1 Score |
|---|---|---|---|---|
| **Custom Random Forest** | **0.86** | **0.90** | **0.88** | **0.88** |
| Linear SVM | 0.80 | 0.84 | 0.77 | 0.80 |
| Logistic Regression | 0.76 | 0.81 | 0.71 | 0.76 |

---

## 📊 Dataset

**Pima Indians Diabetes Dataset** — 768 patient records, 8 features:

| Feature | Description |
|---|---|
| Pregnancies | Number of times pregnant |
| Glucose | Plasma glucose concentration (2-hr oral glucose test) |
| BloodPressure | Diastolic blood pressure (mmHg) |
| SkinThickness | Triceps skin fold thickness (mm) |
| Insulin | 2-hour serum insulin (μU/mL) |
| BMI | Body Mass Index — auto-calculated from height & weight |
| DiabetesPedigreeFunction | Auto-calculated from family history inputs |
| Age | Age in years |

Zero values in Glucose, BloodPressure, SkinThickness, BMI, and Insulin are replaced using **median imputation** per target class.

---

## 📁 Project Structure

```
Diabetes-Prediction-System/
│
├── app.py                  # Flask web app — routes, DPF calculation, BMI calculation
├── algo.py                 # Custom Decision Tree + Random Forest from scratch
├── model.py                # Training script — preprocessing, SMOTE, training, evaluation
├── model.pkl               # Trained Random Forest model
├── scaler.pkl              # Fitted StandardScaler
├── diabetes.csv            # Original Pima Indians dataset
├── updated_diabetes.csv    # Dataset after median imputation
├── resampled_diabetes_unscaled.csv  # Dataset after SMOTE balancing
│
├── templates/
│   ├── index.html          # Input form
│   └── result.html         # Prediction result page
│
├── static/
│   └── background.jpg      # Background image
│
└── requirements.txt
```

---

## 🛠️ Tech Stack

- **Language:** Python 3
- **Web Framework:** Flask
- **ML:** Custom NumPy implementation (no sklearn RandomForest)
- **Data:** Pandas, NumPy
- **Balancing:** SMOTE (imbalanced-learn)
- **Scaling:** StandardScaler (scikit-learn)
- **Frontend:** HTML, CSS, Poppins font

---

## 🚀 Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/SUYOGMAUNI/Diabetes-Prediction-System.git
cd Diabetes-Prediction-System
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Train the model (optional — model.pkl already included)

```bash
python model.py
```

### 4. Run the app

```bash
python app.py
```

Open your browser at: `http://localhost:5000`

---

## 📦 Requirements

```
flask
numpy
pandas
scikit-learn
imbalanced-learn
joblib
seaborn
matplotlib
```

---

## 📄 License

This project was submitted as a Minor Project at **Kantipur Engineering College**, affiliated to Tribhuvan University, March 2025.
