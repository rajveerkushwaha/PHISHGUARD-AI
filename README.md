# 🛡️ PHISHGUARD AI 2.0

**PHISHGUARD AI** is an advanced **AI-powered phishing detection system** designed to protect users from phishing attacks by analyzing URLs and detecting malicious websites.
It integrates **AI/ML models, rule-based heuristics, and external APIs (VirusTotal)** for accurate and real-time detection.

---

## 🚀 Features

* 🔗 **Phishing URL Detection** – Detects suspicious and fraudulent links.
* 🧠 **AI + Rule-based Hybrid** – Uses ML models + intelligence APIs for better accuracy.
* 📊 **Visualization Dashboard** – Interactive Vite + React.js UI for clear results.
* 🗄️ **Database Logging** – Saves results with timestamps in SQLite.
* 🐳 **Dockerized Deployment** – Simple and scalable deployment with Docker.
* 🔒 **Secure Configurations** – `.env` file for API keys & secrets.
* 🧩 **Browser Extension Support** – Chrome extension to check URLs instantly.

---

## 🛠️ Tech Stack

* **Frontend:** Vite + React.js, Node.js, npm
* **Backend:** Python (Flask/FastAPI)
* **Database:** SQLite (default) | PostgreSQL/MySQL (optional)
* **Containerization:** Docker + Docker Compose
* **External APIs:** VirusTotal
* **Browser Extension:** Chrome (Manifest v3)

---

## ⚙️ Installation & Setup

### 🔹 Prerequisites

* Python 3.x installed
* Install [Docker Desktop](https://www.docker.com/products/docker-desktop)
* Enable **WSL2** if using Windows (`wsl --install`)
* Install **Node.js + npm** (for frontend)

  ```bash
  sudo apt update
  sudo apt install nodejs npm
  node -v
  npm -v
  ```
* Install **Google Chrome** (for extension support)

---

### 🔹 Download Project

**Option 1 – Clone Repository (Recommended):**

```bash
git clone https://github.com/rajveer-kushwaha/PHISHGUARD-AI.git
cd PHISHGUARDAI
```

**Option 2 – Download as ZIP (GitHub):**

```bash
unzip PHISHGUARD-AI-main.zip
cd PHISHGUARD-AI-main
```

---

### 🔹 Configure Environment

Create a `.env` file inside `backend/`:

```env
DEBUG=false
HOST=0.0.0.0
PORT=5000
CORS_ORIGINS=*
DATABASE_PATH=/home/ltsu/Downloads/PHISHGUARD_final 2.O/PHISHGUARDAI/backend/database.db
VIRUSTOTAL_API_KEY=your_api_key_here
ENABLE_BERT=false
BERT_MODEL_NAME=distilbert-base-uncased
VT_WEIGHT=0.7
ML_WEIGHT=0.3
```

> ⚠️ **Important:** The `DATABASE_PATH` must point to a **valid, writable location**.
> SQLite cannot create a database file if the folder does not exist or permissions are missing.

---

### 🔹 Run Backend without Virtual Environment

1. Ensure the database folder exists and is writable:

```bash
cd backend
touch database.db
chmod 664 database.db
chmod 755 .
```

2. Install dependencies **system-wide or for your user** (Ubuntu 24.04+ requires `--break-system-packages`):

```bash
pip3 install --break-system-packages -r requirements.txt
```

3. Run the backend:

```bash
python3 ../run_backend.py
```

---

### 🔹 Run Frontend (Vite + React)

1. Install npm dependencies:

```bash
cd frontend
npm install
```

2. Start the Vite development server:

```bash
npm run dev
```

* Vite dev server usually runs at `http://localhost:5173`.
* Supports **hot module reload (HMR)** for faster development.

---

### 🔹 Run with Docker (Optional)

```bash
docker compose up --build
```

---

## 🌐 Access

* **Frontend (Dashboard):** [http://localhost:5173](http://localhost:5173)
* **Backend API:** [http://localhost:5000](http://localhost:5000)
* **Chrome Extension (PhishGuard Lite):**

  1. Open Chrome → `chrome://extensions/`
  2. Enable **Developer Mode**
  3. Click **Load unpacked**
  4. Select `/extension/` folder

---

## 🔒 Security Measures

* Secrets handled via `.env`
* Parameterized SQL queries → protect against SQL Injection
* CORS restricted → only frontend + extension allowed
* Basic rate limiting → prevents API abuse

---

## ⚡ Notes on Common Errors

### SQLite `OperationalError`

If you see:

```
sqlite3.OperationalError: unable to open database file
```

✅ Fix:

1. Ensure the database folder exists.
2. Ensure the `DATABASE_PATH` in `.env` points to a **writable location**.
3. Make the folder and file writable:

```bash
touch /full/path/to/database.db
chmod 664 /full/path/to/database.db
chmod 755 /full/path/to/folder
```

---

## 🚀 Future Enhancements

* Email phishing detection
* Enterprise monitoring dashboard
* Cloud DB support (PostgreSQL/MySQL)
* Offline ML detection model
* Firefox extension support

---

## 👨‍💻 Contributor

* **Rajveer** – Project Developer

---

## 📜 License

Licensed under the **MIT License**.
