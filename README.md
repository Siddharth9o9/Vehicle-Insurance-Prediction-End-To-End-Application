<div align="center">

# 🚗 Vehicle Insurance Prediction
### End-to-End MLOps Application

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776ab?style=flat-square&logo=python&logoColor=white)](https://python.org)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-f7931e?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![Docker](https://img.shields.io/badge/Docker-Containerized-2496ed?style=flat-square&logo=docker&logoColor=white)](https://docker.com)
[![AWS](https://img.shields.io/badge/AWS-EC2-ff9900?style=flat-square&logo=amazonaws&logoColor=white)](https://aws.amazon.com)
[![CI/CD](https://img.shields.io/badge/CI%2FCD-GitHub_Actions-2088ff?style=flat-square&logo=githubactions&logoColor=white)](https://github.com/features/actions)
[![License](https://img.shields.io/badge/License-MIT-10b981?style=flat-square)](LICENSE)

<br/>

> **Predicts whether a customer will purchase vehicle insurance — end-to-end, production-ready.**  
> Full MLOps pipeline from raw data to a Dockerized Flask app deployed on AWS EC2.

</div>

---

## 🎯 Problem Statement

Insurance companies need to identify which existing health insurance customers are likely to also purchase vehicle insurance. This reduces cold outreach, improves conversion rates, and optimises premium pricing strategy.

This application takes customer profile inputs and predicts the **likelihood of insurance purchase** using a trained classification model.

---

## 🏗️ System Architecture

```
Raw Data
   │
   ▼
Data Ingestion ──▶ Data Validation ──▶ Data Transformation
                                               │
                                               ▼
                                       Model Training
                                               │
                                               ▼
                                       Model Evaluation
                                               │
                                               ▼
                                    Flask Web Application
                                               │
                              ┌────────────────┴────────────────┐
                              ▼                                  ▼
                         Docker Image                      CI/CD Pipeline
                              │                           (GitHub Actions)
                              ▼                                  │
                        AWS ECR Registry  ◀────────────────────-─┘
                              │
                              ▼
                         AWS EC2 Server
```

---

## ✨ Features

- **Binary Classification** — Predicts Yes/No insurance purchase likelihood
- **Full MLOps Pipeline** — Automated data ingestion → validation → transformation → training → evaluation
- **Modular Codebase** — Clean `src/` structure with separate components for each pipeline stage
- **Flask Web App** — Simple, responsive UI for real-time predictions
- **Dockerized** — Fully containerized for consistent deployment anywhere
- **CI/CD via GitHub Actions** — Auto-builds Docker image and deploys to AWS EC2 on every push
- **Configurable** — All parameters managed via `config/` — no hardcoding

---

## 🗂️ Project Structure

```
vehicle-insurance-prediction/
│
├── src/
│   ├── components/         # Pipeline stages: ingestion, validation, transformation, training
│   ├── pipeline/           # Training & prediction pipeline orchestration
│   ├── entity/             # Data classes for config and artifact entities
│   └── utils/              # Common utilities
│
├── config/                 # YAML config files for all pipeline parameters
├── notebook/               # EDA and model experimentation notebooks
├── templates/              # Flask HTML templates
├── static/css/             # Frontend styling
│
├── .github/workflows/      # CI/CD pipeline (GitHub Actions → AWS EC2)
│
├── app.py                  # Flask application entry point
├── Dockerfile              # Container definition
├── setup.py                # Package setup
├── pyproject.toml          # Build config
├── requirements.txt        # Dependencies
└── README.md
```

---

## 🚀 Quick Start

### Run Locally

**1. Clone the repo**
```bash
git clone https://github.com/Siddharth9o9/Vehicle-Insurance-Prediction-End-To-End-Application.git
cd Vehicle-Insurance-Prediction-End-To-End-Application
```

**2. Create virtual environment**
```bash
python -m venv venv
source venv/bin/activate        # macOS / Linux
venv\Scripts\activate           # Windows
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**4. Run the training pipeline**
```bash
python demo.py
```

**5. Launch the Flask app**
```bash
python app.py
```
Open `http://localhost:5000` in your browser.

---

### Run with Docker

```bash
# Build the image
docker build -t vehicle-insurance-prediction .

# Run the container
docker run -p 5000:5000 vehicle-insurance-prediction
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **ML & Data** | Python, scikit-learn, pandas, NumPy |
| **Experimentation** | Jupyter Notebook |
| **Web App** | Flask, HTML/CSS |
| **Containerization** | Docker |
| **CI/CD** | GitHub Actions |
| **Cloud** | AWS EC2, AWS ECR |
| **Config Management** | YAML-based config system |

---

## 🔄 MLOps Pipeline Stages

**1. Data Ingestion** — Loads raw dataset, splits into train/test sets, stores artifacts

**2. Data Validation** — Schema checks, null detection, distribution validation against expected schema

**3. Data Transformation** — Feature engineering, encoding, scaling — outputs a transformation artifact

**4. Model Training** — Trains classifier, tunes hyperparameters, saves model artifact

**5. Model Evaluation** — Compares new model against production baseline, promotes only if improved

**6. Prediction Pipeline** — Loads saved model + transformer, runs inference on new inputs from the Flask UI

---

## ⚙️ CI/CD Flow

```
git push ──▶ GitHub Actions triggered
                │
                ▼
           Run tests & lint
                │
                ▼
         docker build & push ──▶ AWS ECR
                                    │
                                    ▼
                            Pull & run on AWS EC2
```

Every push to `main` automatically builds a fresh Docker image, pushes it to ECR, and redeploys on the EC2 instance — zero manual steps.

---

## 📊 Model Details

| Attribute | Detail |
|---|---|
| **Task** | Binary Classification |
| **Target** | Will customer buy vehicle insurance? (Yes / No) |
| **Key Features** | Age, Gender, Vehicle Age, Prior Damage, Prior Insurance, Premium, Sales Channel |
| **Evaluation Metric** | ROC-AUC, F1-Score |

---

## 📄 License

MIT — free to use, modify, and distribute.

---

<div align="center">
  <sub>Built with Python · scikit-learn · Flask · Docker · GitHub Actions · AWS</sub>
</div>