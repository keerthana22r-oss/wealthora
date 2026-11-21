# 💎 Wealthora — Smart Personal Finance & Expense Intelligence Platform

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy?repo=https://github.com/keerthana22r-oss/wealthora)
[![Live Demo](https://img.shields.io/badge/Demo-Live%20Application-brightgreen?style=for-the-badge&logo=render&logoColor=white)](https://wealthora.onrender.com)
[![GitHub Repo](https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/keerthana22r-oss/wealthora)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge)](https://opensource.org/licenses/MIT)

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-4.2%20LTS-092E20?style=flat-square&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=flat-square&logo=mysql&logoColor=white)](https://www.mysql.com/)
[![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3-7952B3?style=flat-square&logo=bootstrap&logoColor=white)](https://getbootstrap.com/)
[![Chart.js](https://img.shields.io/badge/Charts-Chart.js-FF6384?style=flat-square&logo=chartdotjs&logoColor=white)](https://www.chartjs.org/)
[![ReportLab](https://img.shields.io/badge/PDF%20Engine-ReportLab-E74C3C?style=flat-square)](https://www.reportlab.com/)

---

## 📌 Executive Overview

**Wealthora** is an enterprise-grade full-stack personal finance and wealth intelligence platform built with **Django 4.2 LTS** and **MySQL**. It empowers users to take full control over their financial health through automated transaction classification, interactive visualization dashboards, dynamic budget threshold monitoring (80%/100% danger alerts), goal-based savings milestone tracking, recurring subscription leak detection, and on-demand PDF/CSV statements.

Designed with clean MVC/MVT architecture, Wealthora separates business logic into modular domain apps (`transactions`, `dashboard`, `goals`, `subscriptions`, `insights`, `reports`), enforces relational data integrity with foreign keys and database constraints, and visualizes financial velocity using **Chart.js**.

---

## 🎯 UI Preview & Screenshots

### Interactive Financial Dashboard
<p align="center">
  <img width="1913" height="907" alt="Wealthora Dashboard" src="https://github.com/user-attachments/assets/bf3334d9-8b36-47f5-9ca4-eb3a09056c35" />
</p>

### Income & Transaction Management
<p align="center">
  <img width="1914" height="904" alt="Wealthora Income Tracker" src="https://github.com/user-attachments/assets/954efd16-c9b6-4e8c-a1e5-a9e7e9310e9b" />
</p>

---

## ✨ Core Highlights & Key Features

- **🔐 Robust Authentication & Security**:
  - Secure registration, session authentication, CSRF validation, password change hashing (PBKDF2 SHA-256), and strict user-isolated querysets.
- **💳 Multi-Account & Transaction Management**:
  - Full CRUD for income and expense transactions.
  - Category-based tagging with date and keyword filtering.
  - Atomic transactions safeguarding ledger consistency.
- **📊 Interactive Financial Analytics (Chart.js)**:
  - Real-time spending doughnut charts, month-by-month cashflow trend lines, and dynamic summary KPI metrics.
- **🎯 Dynamic Budget Warning System**:
  - Sets per-category monthly limits with real-time spend calculations.
  - Visual color-coded warning states: `Normal (<80%)`, `Warning (80–99%)`, and `Exceeded (100%+)`.
- **🏦 Target-Driven Savings Goals**:
  - Target tracking with animated progress meters and automated formulas calculating monthly contributions required to hit deadlines.
- **🔄 Recurring Subscriptions Tracker**:
  - Tracks repeating expenses (Weekly, Monthly, Quarterly, Annual).
  - Automatically calculates upcoming billing dates and annual cost projections.
- **📑 Financial Statements Export (ReportLab)**:
  - Generates downloadable, styled PDF statements and CSV exports for custom date windows.

---

## 🛠️ Technology Stack Breakdown

| Layer | Technology | Details |
| :--- | :--- | :--- |
| **Backend Framework** | **Python 3 / Django 4.2 LTS** | Clean MVT architecture, Django ORM, decoupled settings |
| **Database** | **MySQL 8.0** | Relational schemas, foreign-key indexing, transactional isolation |
| **Frontend Styling** | **HTML5, CSS3, Bootstrap 5.3** | Responsive dashboard layout, mobile-first navigation |
| **Interactive Visuals** | **Chart.js** | Client-side reactive line, doughnut, and bar charts |
| **Configuration** | **python-decouple** | 12-factor configuration via `.env` file separation |
| **Document Generation** | **ReportLab 5.0** | Dynamic vector PDF rendering for transaction summaries |
| **Icons & Assets** | **Bootstrap Icons** | Scalable SVG icon set across all dashboard widgets |

---

## 🏛️ Project Architecture & Directory Layout

```
wealthora/
├── manage.py                     # Django management utility
├── requirements.txt              # Pinned production dependencies
├── .env.example                  # Environment variable blueprint
├── DEPLOYMENT_NOTES.md           # Cloud deployment instructions (PythonAnywhere / Render)
├── accounts/                     # User authentication, custom profiles, password reset
├── core/                         # Shared utilities, base mixins, template tags
├── dashboard/                    # KPI aggregation, Chart.js feeds, analytical views
├── transactions/                 # Income/Expense CRUD, category tagging, filtering
├── goals/                        # Savings goals, milestone tracking, fund progress
├── subscriptions/                # Recurring payment detection & billing schedule
├── insights/                     # Rule-based spending intelligence & alerts
├── reports/                      # PDF export (ReportLab) & CSV generation
├── static/                       # Custom CSS styles, JS chart modules, images
├── templates/                    # Modular Django templates with base layout inheritance
└── wealthora/                    # Root configuration, WSGI/ASGI, base URLs
```

---

## 💻 Local Development & Quickstart Guide

### Prerequisites
- **Python 3.10+**
- **MySQL Server** (via MySQL CLI, Docker, or XAMPP)
- **Git**

### 1. Clone the Repository
```bash
git clone https://github.com/keerthana22r-oss/wealthora.git
cd wealthora
```

### 2. Environment Configuration
Create a virtual environment and configure your `.env` file:
```bash
# Create and activate virtualenv
python -m venv venv

# Windows (PowerShell):
.\venv\Scripts\Activate.ps1
# macOS/Linux:
# source venv/bin/activate

# Install required packages
pip install -r requirements.txt

# Create environment configuration
cp .env.example .env
```

Edit `.env` with your database credentials:
```ini
DEBUG=True
SECRET_KEY=your-secure-secret-key-here
DB_NAME=wealthora_db
DB_USER=root
DB_PASSWORD=your_mysql_password
DB_HOST=127.0.0.1
DB_PORT=3306
```

### 3. Initialize Database & Run Server
```bash
# Create the database in MySQL:
# mysql -u root -p -e "CREATE DATABASE wealthora_db CHARACTER SET utf8mb4;"

# Run migrations
python manage.py migrate

# Create superuser admin
python manage.py createsuperuser

# Start development server
python manage.py runserver
```

Open **`http://127.0.0.1:8000`** in your browser.

---

## 🚀 One-Click Cloud Deployment (Render Blueprint)

Wealthora includes a native **`render.yaml`** Infrastructure-as-Code blueprint with automated PostgreSQL provisioning:

1. Click the **Deploy to Render** button at the top, or log in to **[dashboard.render.com](https://dashboard.render.com)**.
2. Click **New +** ➔ **Blueprint**.
3. Select your repository: **`keerthana22r-oss/wealthora`**.
4. Click **Apply**:
   - Render automatically creates the **PostgreSQL database** (`wealthora-db`).
   - Links the connection string via `DATABASE_URL`.
   - Runs `pip install`, compiles static assets with **WhiteNoise**, and applies database migrations.
   - Starts the production WSGI server with **Gunicorn**.
5. Your live application will be live at `https://wealthora-xxxx.onrender.com` in ~2 minutes!

---

## 🔮 Roadmap & Future Enhancements

- [ ] **Automated Bank Feed Sync**: Integrate Plaid API for automated bank statement synchronization.
- [ ] **AI-Powered Financial Advisor**: Integrate Gemini Flash to provide personalized saving recommendations based on monthly spend variance.
- [ ] **Split-Expense Sharing**: Peer-to-peer bill splitting with balance settlement calculations.

---

## 👩‍💻 Author & Contact

**Keerthana K R**  
Full-Stack & AI Software Engineer  

- **GitHub:** [@keerthana22r-oss](https://github.com/keerthana22r-oss)
- **Email:** [keerthana22r@gmail.com](mailto:keerthana22r@gmail.com)
- **LinkedIn:** [linkedin.com/in/keerthanakr](https://www.linkedin.com)

---

## 📄 License

This project is open-source and distributed under the [MIT License](https://opensource.org/licenses/MIT).
