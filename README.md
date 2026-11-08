<<<<<<< HEAD
# 🎓 AI Career Guidance System
### **Course: CSE276 — Artificial Intelligence Foundations (CA1 Project-Based Assignment)**
### **Problem Statement P09 | Reference: Smart India Hackathon (SIH 2024 - SIH1781)**

---

## 📌 Executive Summary

The **AI Career Guidance System** is an end-to-end, explainable artificial intelligence platform designed to deliver personalized educational pathways, career recommendations, and quantitative skill-gap roadmaps for students at three pivotal milestones:
1. **Secondary Education (After Class 10):** Stream selection (Science PCM/PCB, Commerce, Humanities) and polytechnic diploma routes.
2. **Higher Secondary Education (After Class 12):** Undergraduate degrees, national entrance examinations (JEE, NEET, CUET, CLAT, NATA, etc.), and industry career paths.
3. **Higher Education & Graduates (Undergraduate / Working):** Postgraduate specializations (M.Tech, MBA, M.Sc), research programs (GATE, UGC-NET), civil services, and technical career transitions.

Built specifically for the **CSE276: Artificial Intelligence Foundations** curriculum, this system replaces naive static rules with a **multi-model Machine Learning ensemble**, **surrogate Explainable AI (XAI) feature attributions**, and **instance-based nearest-neighbor retrieval** grounded in the official **O*NET 31.0 Occupational Database**.

---

## 🌟 Key System Capabilities

- **Multi-Model Machine Learning Engine:**
  - **Random Forest Classifier (Ensemble Bagging):** 150 estimators capturing non-linear feature splits and computing Gini-impurity global feature importance.
  - **HistGradientBoosting Classifier (Ensemble Boosting):** Sequential gradient boosting on continuous multi-feature tabular data.
  - **Deep Multi-Layer Perceptron (MLP Neural Network):** 3-layer deep architecture `(128, 64, 32)` with ReLU activations, Adam optimization, and early stopping.
  - **Calibrated Support Vector Machine (Linear SVM):** Maximum-margin hyperplanes calibrated with Platt/sigmoid probability scaling.
  - **O*NET K-Nearest Neighbors (KNN Recommender):** Metric cosine-distance retrieval across the 1,016 O*NET occupational requirement vectors.
  - **Hybrid AI Soft-Voting Ensemble:** Fused meta-recommender achieving **84.9% Top-1**, **99.8% Top-3**, and **100.0% Top-5** recommendation accuracy.
- **Explainable AI (XAI) Attribution Engine:**
  - Local feature attribution calculating exact positive decision drivers (e.g. *Mathematics Performance +24.5%*, *Programming & Algorithmic Design +18.2%*) and growth areas/limiting penalties.
  - Multi-dimensional domain breakdown: Academic Fit, Foundational Skills Fit, and Holland RIASEC Congruence.
- **Quantitative Skill-Gap Analysis & Action Roadmaps:**
  - Calculates mathematical skill gap: $\Delta = \text{Current Skill Level} - \text{O*NET Required Industry Level}$.
  - Visualizes skill radar benchmarks and prioritizes urgent competencies.
  - Generates personalized 4-week structured milestone action plans with free verified resources (NPTEL, SWAYAM, NCERT, Khan Academy, freeCodeCamp).
- **Accredited Stage-Specific Pathways:**
  - Roadmaps aligned with national regulatory bodies: **CBSE, NCERT, AICTE, UGC, NTA, NMC, BCI, and NCS**.
- **Interactive Multi-Model Hub & Benchmarking Dashboard:**
  - Live benchmarking leaderboard, accuracy comparisons (Top-1, Top-3, Top-5), feature importance charts, and on-demand model retraining.
- **Production-Ready & Fully Deployable:**
  - Pre-trained serialized models (`.joblib`), `Dockerfile`, `docker-compose.yml`, `render.yaml`, `Procfile`, `start.sh`, and `start.bat`.

---

## 🧠 Machine Learning Architecture & Benchmarks

The system was trained and evaluated on a **stratified synthetic student-profile dataset (5,000 records, 29 standardized features, 20 curated primary career classes)**:

| Model Architecture | Test Accuracy | Top-3 Accuracy | Top-5 Accuracy | Macro F1 | 5-Fold Cross-Validation |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Random Forest (Bagging)** | 84.60% | 99.50% | 99.80% | 0.842 | 85.6% ± 0.8% |
| **Gradient Boosting (HistGB)** | 84.70% | 99.40% | 99.90% | 0.846 | 85.8% ± 1.1% |
| **Deep Neural Network (MLP)** | 84.50% | **100.00%** | **100.00%** | 0.836 | 85.2% ± 1.1% |
| **Support Vector Machine (SVM)** | 84.60% | 99.40% | 100.00% | 0.842 | 85.1% ± 1.0% |
| **Hybrid AI Ensemble (Fused)** | **84.90%** | **99.80%** | **100.00%** | **0.847** | **Fused Meta-Model** |

### Mathematical Hybrid Ensemble Formulation:
$$P_{\text{Ensemble}}(C_j \mid \vec{x}) = 0.30 \cdot P_{\text{RF}}(C_j) + 0.30 \cdot P_{\text{GB}}(C_j) + 0.25 \cdot P_{\text{MLP}}(C_j) + 0.15 \cdot P_{\text{SVM}}(C_j)$$

### Final Multi-Modal Score Fusion:
$$\text{Score}(C_j) = 0.50 \cdot P_{\text{Ensemble}}(C_j) + 0.30 \cdot S_{\text{Domain}}(\vec{x}, C_j) + 0.20 \cdot \text{Sim}_{\text{KNN}}(\vec{x}, \vec{v}_{\text{O*NET}})$$

---

## 🛠️ Technology Stack

- **Core AI & ML:** Python 3.10+ / 3.13, Scikit-Learn 1.7+, NumPy, SciPy, Joblib
- **Web Interface:** Streamlit (>= 1.36.0)
- **Data Visualizations:** Plotly Graph Objects (Radar, Polar, Bar Charts)
- **Automated Testing:** Pytest (32 automated unit and integration tests)
- **Occupational Knowledge Base:** National Center for O*NET Development (O*NET 31.0 Database)
- **Containerization & Cloud:** Docker, Docker Compose, Render, Heroku / Railway Procfile

---

## 📁 Repository Structure

```text
ai-career-guidance-system/
├── app.py                          # Streamlit interactive EdTech & AI dashboard
├── ml_models.py                    # Multi-Model AI Suite & inference pipeline
├── train_models.py                 # Training script, benchmarking, & telemetry serialization
├── dataset_generator.py            # Synthetic student-profile generator (5,000 records)
├── explainability.py               # Explainable AI (XAI) feature attribution & decomposition
├── career_engine.py                # Hybrid multi-modal scoring engine & dimension fusion
├── assessment.py                   # Data models, RIASEC mappings, & student profiles
├── pathways_engine.py              # Quantitative skill-gap analysis & 4-week roadmaps
├── data_loader.py                  # Schema-safe O*NET CSV and JSON catalog loader
├── requirements.txt                # Python package dependencies
├── Dockerfile                      # Production Docker container definition
├── docker-compose.yml              # Local/Production Docker Compose service
├── Procfile                        # Cloud deployment runner (Heroku, Render, Railway)
├── render.yaml                     # Render Infrastructure-as-Code blueprint
├── start.bat                       # Windows one-click launcher
├── start.sh                        # Linux / macOS launcher
├── models/
│   ├── career_models.joblib        # Pre-trained serialized AI model bundle
│   └── model_metrics.json          # Benchmarking metrics & telemetry
├── data/
│   ├── synthetic_student_profiles.csv # Generated 5,000 student training records
│   ├── demo_profiles.csv           # Verified student demo profiles across stages
│   ├── careers.json                # 20 curated primary career profiles
│   ├── pathways.json               # Accredited educational pathways (Class 10, 12, UG)
│   ├── interest_mappings.json      # RIASEC Holland mappings
│   ├── subject_mappings.json       # O*NET knowledge domain mappings
│   └── onet/                       # O*NET 31.0 occupational dataset tables
└── tests/
    ├── test_ai_models.py           # Verification of ML inference, XAI, & synthetic data
    ├── test_career_engine.py       # Engine scoring, bounds, and sensitivity tests
    ├── test_pathways_engine.py     # Skill-gap & roadmap validation tests
    ├── test_assessment_and_export.py # Assessment serialization & dossier export tests
    └── test_data_validation.py     # Dataset integrity & schema conformance tests
```

---

## 🚀 Quick Start & Installation

### 1. Clone or Open the Repository
```bash
cd ai-career-guidance-system
```

### 2. Set Up a Python Virtual Environment
```bash
python -m venv .venv

# Windows (PowerShell):
.\.venv\Scripts\Activate.ps1

# Linux / macOS:
source .venv/bin/activate
```

### 3. Install Required Dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the Application
```bash
streamlit run app.py
```
Open [http://localhost:8501](http://localhost:8501) in your browser.

---

## 🧪 Running Automated Tests

Run the full pytest suite (32 tests):
```bash
python -m pytest
```

---

## 🔄 Retraining the AI Models

You can retrain and benchmark all models at any time:
```bash
python train_models.py
```
*(Alternatively, use the interactive "🔄 Retrain and Benchmark All Models" button inside the **🧠 AI & ML Models Hub** tab in the web interface).*

---

## 🐳 Docker Deployment

Build and run the application via Docker:
```bash
docker build -t ai-career-guidance-system .
docker run -p 8501:8501 ai-career-guidance-system
```
Or with Docker Compose:
```bash
docker-compose up --build
```
Access the application at [http://localhost:8501](http://localhost:8501).

---

## ☁️ Cloud Deployment (Render / Heroku / Streamlit Cloud)

- **Render:** Connect repository and choose "Web Service" using `render.yaml` or Docker.
- **Heroku / Railway:** Automatically recognized via `Procfile` and `requirements.txt`.
- **Streamlit Community Cloud:** Point repository to `app.py`.

---

## 📜 Academic Integrity & License

This project was built for **CSE276: Artificial Intelligence Foundations** and references the **Smart India Hackathon (SIH 2024 - SIH1781)** challenge. Occupational data is provided under Creative Commons Attribution 4.0 by the National Center for O*NET Development.
=======
# AI_CAREER_GUIDANCE
SYSTEM
>>>>>>> 99b9b30b31c1f232a05166756b4ff3935cced33c
