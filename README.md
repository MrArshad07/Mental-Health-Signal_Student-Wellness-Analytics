# 🧠 Mental Health Signal — Student Wellness Analytics

> **An end-to-end machine learning application that predicts a student mental-health score from behavioral, academic, digital-usage and lifestyle signals.**

[![Live Demo](https://img.shields.io/badge/Live-Demo-success?style=for-the-badge)](https://mental-health-score-prediction-1-ycv1.onrender.com/)
[![Python](https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge\&logo=python)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-API-009688?style=for-the-badge\&logo=fastapi)](https://fastapi.tiangolo.com/)
[![Scikit--learn](https://img.shields.io/badge/Scikit--learn-ML-F7931E?style=for-the-badge\&logo=scikit-learn)](https://scikit-learn.org/)
[![Render](https://img.shields.io/badge/Deployed-Render-46E3B7?style=for-the-badge)](https://render.com/)

## 🚀 Live Application

**Try the deployed application:**

👉 https://mental-health-score-prediction-1-ycv1.onrender.com/

## 🖥️ Application Preview

<img width="1920" height="1080" alt="Screenshot (168)" src="https://github.com/user-attachments/assets/116b2d0c-074d-4962-8e0d-6b0a85640a53" />
<img width="1920" height="1080" alt="Screenshot (169)" src="https://github.com/user-attachments/assets/80fd6305-41fe-4112-ba0f-efeaec0eaf14" />

The application provides an interactive interface where users enter behavioral, academic, digital-usage and lifestyle information and receive a predicted mental-health score on a 0–10 scale.

> ⚠️ **Important:** This project is for educational and informational purposes only. It is not a clinical assessment, diagnosis, or medical recommendation.

---

## 📌 Project Overview

Mental Health Signal is an end-to-end machine learning project designed to demonstrate how a regression model can be transformed into a deployable data product.

The system takes student-level signals such as:

* Age
* Gender
* Academic level
* Study hours
* Daily screen time
* Daily phone unlocks
* Physical activity
* Sleep duration
* Perceived stress
* Most-used social platform
* Primary purpose of social-media use
* Country/grouped country

and generates a predicted mental-health score.

The project covers the complete ML lifecycle:

```text
Raw Data
   ↓
Data Cleaning & EDA
   ↓
Feature Engineering
   ↓
Preprocessing Pipeline
   ↓
Model Training
   ↓
Model Comparison
   ↓
Hyperparameter Tuning
   ↓
Model Evaluation
   ↓
Model Serialization
   ↓
FastAPI REST API
   ↓
HTML/CSS/JavaScript Frontend
   ↓
Render Deployment
```

---

## 🎯 Business / Real-World Problem

Student wellbeing can be influenced by multiple interacting behavioral and lifestyle factors.

The goal of this project is to demonstrate how machine learning can transform these signals into a simple predictive analytics application.

Instead of stopping at model training in a notebook, this project demonstrates the complete transition from:

**Machine Learning Model → API → User Interface → Cloud Deployment**

---

## 🧠 Machine Learning Approach

### Problem Type

**Supervised Learning — Regression**

### Target

```text
Mental_Health_Score
```

### Input Features

| Category         | Features                         |
| ---------------- | -------------------------------- |
| Profile          | Age, Gender, Country             |
| Academic         | Academic Level, Study Hours      |
| Digital Behavior | Daily Usage Hours, Daily Unlocks |
| Platform         | Most Used Platform               |
| Usage Purpose    | Primary Purpose of Use           |
| Lifestyle        | Sleep Hours, Physical Activity   |
| Stress           | Perceived Stress Level           |

---

## ⚙️ Machine Learning Pipeline

The project uses a preprocessing and modeling workflow designed to keep transformations consistent between training and prediction.

```text
Input Features
      │
      ├── Numerical Features
      │       ↓
      │   Transformation
      │       ↓
      │   Scaling
      │
      ├── Categorical Features
      │       ↓
      │   Encoding
      │
      └── Feature Engineering
              ↓
       Combined Feature Matrix
              ↓
       Regression Model
              ↓
      Mental Health Score
```

The trained pipeline/model is serialized and loaded by the FastAPI backend during application startup.

---

## 🏆 Model Selection

Multiple regression algorithms were evaluated during experimentation.

| Model                   |   R² Score |
| ----------------------- | ---------: |
| Extra Trees Regressor   | **0.8907** |
| Random Forest Regressor |     0.8521 |
| HistGradientBoosting    |     0.8286 |
| Gradient Boosting       |     0.7854 |
| Decision Tree           |     0.7220 |
| Linear/Ridge            |    ~0.7178 |

### Final Model

**Extra Trees Regressor**

Hyperparameter tuning was performed to improve model generalization.

Final reported evaluation:

| Metric |      Score |
| ------ | ---------: |
| R²     | **0.8893** |
| MAE    | **0.3234** |
| RMSE   | **0.4409** |

> Metrics are based on the project's held-out evaluation setup.

---

## 🌐 Application Architecture

```text
                    ┌──────────────────────┐
                    │      User Input      │
                    │   HTML / CSS / JS    │
                    └──────────┬───────────┘
                               │
                               │ POST /predict
                               ▼
                    ┌──────────────────────┐
                    │      FastAPI         │
                    │   Request Validation │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │  ML Model / Pipeline │
                    │   Scikit-learn       │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │ Predicted Score 0–10 │
                    └──────────────────────┘
```

---

## 🔌 API

### Health / Root Endpoint

```http
GET /
```

### Prediction Endpoint

```http
POST /predict
```

Example request:

```json
{
  "age": 21,
  "gender": "Male",
  "country": "India",
  "academic_level": "Undergraduate",
  "most_used_platform": "Instagram",
  "purpose_of_use": "Education",
  "avg_daily_usage_hours": 5.5,
  "daily_unlocks": 60,
  "study_hours": 6,
  "physical_activity_hours": 1,
  "sleep_hours_per_night": 7,
  "stress_level": "Medium"
}
```

Example response:

```json
{
  "predicted_mental_health_score": 6.78
}
```

---

## 🖥️ Frontend

The frontend was designed as a focused student-wellness analytics interface rather than a generic form.

It includes:

* Responsive form interface
* Profile section
* Academic and digital-habit inputs
* Lifestyle and stress inputs
* Client-side validation
* Loading state
* Prediction result state
* Score visualization
* Error handling
* Reset / retry interaction

---

## 🛠️ Tech Stack

### Machine Learning

* Python
* Pandas
* NumPy
* Scikit-learn
* Joblib

### Backend

* FastAPI
* Pydantic
* Uvicorn

### Frontend

* HTML5
* CSS3
* JavaScript

### Deployment

* Render
* GitHub

---

## 📁 Project Structure

```text
Mental-Health-Score-Prediction-Model/
│
├── main.py
├── mental_health_model.pkl
├── requirements.txt
├── README.md
├── LICENSE
├── .gitignore
│
├── templates/
│   └── index.html
│
├── static/
│   ├── style.css
│   └── script.js
│
├── notebooks/
│   └── Mental_Health_Score_Predictor.ipynb
│
├── data/
│   └── README.md
│
└── screenshots/
    ├── dashboard.png
    ├── prediction.png
    └── architecture.png
```

---

## 🚀 Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/MrArshad07/Mental-Health-Score-Prediction-Model.git
cd Mental-Health-Score-Prediction-Model
```

### 2. Create a virtual environment

Windows:

```bash
python -m venv venv
venv\Scripts\activate
```

macOS/Linux:

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Start FastAPI

```bash
uvicorn main:app --reload
```

### 5. Open the application

```text
http://127.0.0.1:8000
```

API documentation:

```text
http://127.0.0.1:8000/docs
```

---

## ☁️ Deployment

The application is deployed using Render.

Production flow:

```text
GitHub Repository
       ↓
Render Build
       ↓
Python Environment
       ↓
Uvicorn
       ↓
FastAPI Application
       ↓
Live Web Application
```

### Production Command

```bash
uvicorn main:app --host 0.0.0.0 --port $PORT
```

---

## 🔍 Engineering Highlights

This project demonstrates more than model training.

### 1. Input validation

FastAPI/Pydantic validates numerical ranges and categorical values before inference.

### 2. Consistent feature handling

The backend constructs a structured DataFrame matching the model's expected feature schema.

### 3. Categorical handling

Categorical variables such as gender, academic level, platform, purpose and grouped country are handled as model inputs.

### 4. API-based inference

The trained model is exposed through a REST endpoint instead of running only inside a notebook.

### 5. Frontend-backend integration

JavaScript communicates with the FastAPI prediction endpoint and dynamically displays the result.

### 6. Cloud deployment

The complete application is publicly accessible through Render.

---

## 📊 What I Learned

Through this project I practiced:

* End-to-end ML workflow
* Regression modeling
* Feature preprocessing
* Categorical encoding
* Model comparison
* Hyperparameter tuning
* Model serialization
* REST API development
* Pydantic validation
* Frontend/backend integration
* Git/GitHub workflow
* Cloud deployment
* Production-oriented project structure

---

## 👨‍💻 Author

**Arshad Hanif Sayyad**

Aspiring Machine Learning / Data Science professional focused on building practical end-to-end machine learning applications.

### Connect

* GitHub: https://github.com/MrArshad07
* Live Project: https://mental-health-score-prediction-1-ycv1.onrender.com/

---

## ⭐ If you found this project useful

Consider giving the repository a ⭐ and exploring the implementation.

---

### Disclaimer

This application is intended for educational and informational purposes only. It does not provide medical advice, diagnosis, treatment, or clinical assessment.

