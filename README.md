# 🛡️ PHISHGUARD AI 2.0

**PHISHGUARD AI** is an advanced **AI-powered phishing detection system** designed to protect users from phishing attacks by analyzing URLs and detecting malicious websites.  
It integrates **AI/ML models, rule-based heuristics, and external APIs (VirusTotal, PhishTank)** for accurate and real-time detection.  

---

## 🚀 Features
- 🔗 **Phishing URL Detection** – Detects suspicious and fraudulent links.  
- 🧠 **AI + Rule-based Hybrid** – Uses ML models + intelligence APIs for better accuracy.  
- 📊 **Visualization Dashboard** – Interactive React.js UI for clear results.  
- 🗄️ **Database Logging** – Saves results with timestamps in SQLite.  
- 🐳 **Dockerized Deployment** – Simple and scalable deployment with Docker.  
- 🔒 **Secure Configurations** – `.env` file for API keys & secrets.  
- 🧩 **Browser Extension Support** – Chrome extension to check URLs instantly.  

---

## 🛠️ Tech Stack
- **Frontend:** React.js  
- **Backend:** Python (Flask/FastAPI)  
- **Database:** SQLite (default) | PostgreSQL/MySQL (optional)  
- **Containerization:** Docker + Docker Compose  
- **External APIs:** VirusTotal, PhishTank  
- **Browser Extension:** Chrome (Manifest v3)  

---

## 📂 Project Structure
```
PHISHGUARDAI/
│── backend/             # Backend (Flask/FastAPI)
│   ├── app.py           # Main server
│   ├── config.py        # Configurations
│   ├── db.py            # Database handler
│   ├── database.db      # SQLite DB
│   ├── requirements.txt # Dependencies
│   └── Dockerfile       # Backend Docker setup
│
│── frontend/            # React.js frontend
│   ├── package.json     # Frontend dependencies
│
│── extension/           # Chrome Extension
│   ├── manifest.json    # Extension config (Manifest v3)
│   ├── popup.html       # Extension popup UI
│   ├── popup.js         # Logic for sending requests
│   ├── icons/           # Extension icons
│
│── docker-compose.yml   # Docker Compose config
│── run_backend.py       # Quick backend runner
│── README.md            # Documentation
```

---

## ⚙️ Installation & Setup

### 🔹 Prerequisites
- Install [Docker Desktop](https://www.docker.com/products/docker-desktop)  
- Enable **WSL2** if using Windows (`wsl --install`)  
- Install **Google Chrome** (for extension support)  

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

### 🔹 Configure Environment
Create `.env` file inside `backend/`:
```
API_KEY_VIRUSTOTAL=your_api_key_here
API_KEY_PHISHTANK=your_api_key_here
```

### 🔹 Run with Docker (Recommended)
```bash
docker compose up --build
```

### 🔹 Run without Docker
Backend:
```bash
cd backend
pip install -r requirements.txt
python app.py
```
Frontend:
```bash
cd frontend
npm install
npm start
```

---

## 🌐 Access
- **Frontend (Dashboard):** http://localhost:3000  
- **Backend API:** http://localhost:5000  
- **Chrome Extension (PhishGuard Lite):**  
  1. Open Chrome and go to `chrome://extensions/`  
  2. Enable **Developer Mode** (top right corner)  
  3. Click **Load unpacked**  
  4. Select the `/extension/` folder  

---

## 📊 System Architecture

```mermaid
flowchart TD
    A[User Input: Suspicious URL] --> B[Frontend (React.js Dashboard)]
    A --> J[Chrome Extension]
    J --> C[Backend (Flask/FastAPI)]
    B --> C
    C --> D[Phishing Detection Engine]
    D --> E[Rule-based Checks]
    D --> F[AI/ML Model]
    D --> G[External Threat APIs (VirusTotal, PhishTank)]
    E --> H[Database Logging]
    F --> H
    G --> H
    H --> I[Results → Dashboard/Extension]
```

---

## 🔒 Security Measures
- Secrets handled via `.env`, not hardcoded.  
- Parameterized SQL queries → protection against SQL Injection.  
- CORS restricted → only frontend + extension allowed.  
- Basic rate limiting → prevents API abuse.  

---

## 🚀 Future Enhancements
- **Email phishing detection** (headers, body, links).  
- **Enterprise monitoring dashboard**.  
- **Cloud DB support** (PostgreSQL/MySQL).  
- **Offline ML detection model** (no API dependency).  
- **Firefox extension** support.  

---

## 🖼️ Workflow Overview (High-level)

```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant Extension
    participant Backend
    participant DetectionEngine
    participant APIs
    participant DB

    User->>Extension: Right-click / Check URL
    Extension->>Backend: Send URL
    User->>Frontend: Submit suspicious URL
    Frontend->>Backend: Send request
    Backend->>DetectionEngine: Process URL
    DetectionEngine->>APIs: Query VirusTotal & PhishTank
    DetectionEngine->>DB: Log result with timestamp
    DetectionEngine->>Frontend: Return detection result
    DetectionEngine->>Extension: Return detection result
    Frontend->>User: Display results
    Extension->>User: Show popup notification
```

---

## 👨‍💻 Contributor
- **Rajveer** – Project Developer  

---

## 📜 License
Licensed under the **MIT License**.  
