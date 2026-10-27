# 🛡️ ChurnSense AI: Predictive Analytics & Retention Intelligence Platform

**ChurnSense AI** is an enterprise customer attrition intelligence platform that couples ensemble machine learning (XGBoost, Random Forest, Logistic Regression) with advanced LLM reasoning (Google Gemini) to identify high-risk customer accounts, diagnose behavioral drivers, and automate bilingual retention maneuvers in real time.

## 🏗️ Technical Architecture

* **Backend Engine**: Asynchronous FastAPI service running on Python 3.11 with high-throughput inference endpoints and automatic OpenAPI/Swagger documentation.
* **Data Science Core**: Stacked ensemble classification aggregating calibrated probabilities from XGBoost, Random Forest, and regularized Logistic Regression with 5-fold cross-validation.
* **Explainability Layer**: Dynamic feature attribution scoring factors like contract vulnerability, technical friction index, and tenure stability.
* **Intelligence Layer**: Google Gemini integration for automated strategic audits, risk driver breakdowns, and bilingual (English & Hindi) retention playbooks.
* **Data Layer**: MongoDB (Atlas Cloud / Local) for persistent historical audit logs and customer records via async Motor drivers.
* **Frontend Interface**: Reactive, single-page dashboard built with React 19, TypeScript, Vite, and Tailwind CSS.

## 🚀 Live Cloud Deployment

| Service | Component | URL |
| :--- | :--- | :--- |
| **Frontend UI** | React Static Site | `https://churnsense-ui.onrender.com` |
| **Backend API** | FastAPI Web Service | `https://churnsense-ai-3khl.onrender.com` |
| **API Docs (Swagger UI)** | Interactive Documentation | `https://churnsense-ai-3khl.onrender.com/docs` |

## ⚙️ Environment Variables

Create a `.env` file in the project root (or configure them in your hosting provider):

```env
# Google Gemini API
API_KEY=AIzaSyYourGeminiApiKeyHere
GEMINI_API_KEY=AIzaSyYourGeminiApiKeyHere

# MongoDB Database Connection
MONGODB_URI=mongodb+srv://<user>:<password>@cluster0.xxxx.mongodb.net/churnsense_ai?retryWrites=true&w=majority

# Security & JWT
JWT_SECRET=your_32_character_jwt_secret_key

# Python Path (for Backend Module Resolution)
PYTHONPATH=.:backend

# Optional SMTP Configuration (Defaults to console mock mode if omitted)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=notifications@yourdomain.com
SMTP_PASS=your_email_app_password
```

## 💻 Local Quickstart

### Prerequisites

* Python 3.11
* Node.js (v18+) & NPM
* Astral `uv` (recommended) or `pip`
* MongoDB (Local instance or MongoDB Atlas cloud connection)

### 1. Backend Setup (FastAPI)

#### Using Astral `uv` (Fastest, All-in-One):

```zsh
# Create virtual environment and install dependencies in one command
uv venv .venv --python 3.11 && source .venv/bin/activate && uv pip install -r requirements.txt

# Start the API server
export PYTHONPATH=".:backend"
python -m uvicorn backend.main:app --port 8000 --reload
```

#### Using Standard `venv` & `pip`:

```zsh
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt

export PYTHONPATH=".:backend"
python -m uvicorn backend.main:app --port 8000 --reload
```

The API will be available at `http://localhost:8000`, with interactive Swagger UI at `http://localhost:8000/docs`.

### 2. Frontend Setup (React & Vite)

In a separate terminal window:

```zsh
# Install frontend packages
npm install

# Start development server
npm run dev
```

Open `http://localhost:5173` in your browser to access the dashboard.

### 3. Production Build

To bundle the frontend for production:

```zsh
npm run build
```

Compiled static assets are generated in the `dist/` directory.

## 📡 API Reference Overview

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/` | Service health status and pipeline verification |
| `POST` | `/api/v1/auth/register` | Register new analyst account |
| `POST` | `/api/v1/auth/verify-otp` | Verify OTP and issue JWT bearer token |
| `GET` | `/api/v1/auth/me` | Fetch authenticated user profile |
| `POST` | `/api/v1/analytics/predict` | Run stacked ensemble inference & LLM strategic audit |
| `GET` | `/api/v1/analytics/history` | Retrieve historical customer risk logs |

Full interactive schemas and payload testing are available via `/docs`.

## 📜 License

This project is open-source and available under the MIT License.
