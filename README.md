<div align="center">

# 🌊 CarbonScope

### Real-Time Digital Carbon Footprint Tracker & Blue Carbon Marine Project Registry

[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-007ACC?style=for-the-badge&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)](https://vitejs.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![Flask](https://img.shields.io/badge/Flask-Python-000000?style=for-the-badge&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![Google APIs](https://img.shields.io/badge/Google_APIs-Gmail_·_Drive_·_YouTube-4285F4?style=for-the-badge&logo=google&logoColor=white)](https://console.cloud.google.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)

[![Demo Video](https://img.shields.io/badge/Demo_Video-Google_Drive-4285F4?style=for-the-badge&logo=google-drive)](https://drive.google.com/file/d/15MGhlgkW2ATjjL0ZTP2NJRyQtvw_NMYU/view?usp=drivesdk)

</div>

---

## 🌐 Demo

| | Link |
|---|---|
| 🎬 **Demo Video** | [Watch on Google Drive](https://drive.google.com/file/d/15MGhlgkW2ATjjL0ZTP2NJRyQtvw_NMYU/view?usp=drivesdk) |

> [!WARNING]
> **This project is not deployed publicly.** It integrates with Google APIs (Gmail, Drive, YouTube Data API v3) which require OAuth credentials and incur billing beyond free-tier limits. To try it, please **run it locally** following the [Getting Started](#-getting-started) steps below — it works fully in a local setup, including a simulation mode if no credentials are provided.

---

## 🚀 What is This?

**CarbonScope** is a full-stack web application built for **HackX** that tracks real-time digital carbon footprints and blue carbon (marine) project data. It connects to your Google account (Gmail, Drive, YouTube) to estimate CO₂ emissions from digital activities, while also providing a verified registry of marine carbon sequestration projects.

---

## ✨ Key Features

| Feature | Description |
|--------|-------------|
| 🌍 **Digital Carbon Tracker** | Calculates your daily CO₂ footprint from emails sent, cloud storage used, and video streaming hours via Google APIs |
| 📈 **Carbon Trend Charts** | Visualizes 6-month digital carbon vs. offset trends using Recharts |
| 📅 **Weekly Breakdown** | Shows day-by-day carbon totals over the past 7 days |
| 🌊 **Marine Project Registry** | Powered by the NCCR Marine dataset (500 records), with pagination, filtering, and per-project verification |
| ✅ **Admin Verification Flow** | New projects start as "Pending"; admins can verify them via API |
| 🔗 **Google API Actions** | Enables smart email scheduling, YouTube streaming optimization, and Google Drive file archiving |
| 🔒 **User Authentication** | Signup/login with hashed passwords using Flask-SQLAlchemy + SQLite |
| ⚙️ **Settings Panel** | User can update profile, notification preferences, and privacy settings |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        BROWSER                              │
│   React 18 + TypeScript + Vite + Tailwind CSS               │
│   • Dashboard — digital carbon KPIs + trend charts          │
│   • Marine Registry — paginated + filtered project table    │
│   • Settings — profile, notifications, privacy              │
└────────────────────────┬────────────────────────────────────┘
                         │ HTTP (JSON) via proxy
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                    Flask Backend                             │
│                                                             │
│  /api/total_co2     — today's total CO₂ footprint           │
│  /api/carbonchart   — 6-month carbon vs. offset data        │
│  /api/data          — paginated marine project records      │
│  /api/verify/<id>   — admin verification endpoint           │
│  /execute_plan      — trigger Google API action             │
│  /signup + /login   — user auth with hashed passwords       │
│                                                             │
│  Google OAuth → Gmail API + Drive API + YouTube API         │
│  Simulation Mode if credentials.json is absent              │
└─────────────────────────────────────────────────────────────┘
```

---

## 🧩 Tech Stack

### Frontend
- **[React 18](https://react.dev)** — Component-based UI framework
- **[TypeScript](https://www.typescriptlang.org)** — Full type safety across components
- **[Vite](https://vitejs.dev)** — Fast build tool and dev server
- **[Tailwind CSS](https://tailwindcss.com)** — Utility-first styling
- **[shadcn/ui](https://ui.shadcn.com)** — Radix UI primitives
- **[Recharts](https://recharts.org)** — Carbon trend and breakdown charts
- **[TanStack React Query](https://tanstack.com/query)** — Data fetching and state
- **[React Router DOM v6](https://reactrouter.com)** — Client-side routing

### Backend
- **[Flask](https://flask.palletsprojects.com)** — Python web framework
- **[Flask-SQLAlchemy](https://flask-sqlalchemy.palletsprojects.com)** — ORM + SQLite database
- **[Flask-CORS](https://flask-cors.readthedocs.io)** — Cross-origin support

### Integrations & Data
- **[Gmail API](https://developers.google.com/gmail/api)** — Email count for CO₂ estimation
- **[Google Drive API](https://developers.google.com/drive)** — Cloud storage usage
- **[YouTube Data API v3](https://developers.google.com/youtube/v3)** — Watch hours tracking
- **NCCR Marine Sample Dataset** — 500-record CSV of marine carbon sequestration projects

---

## 📁 Project Structure

```
CarbonScopeHackx/
├── backend/
│   ├── app.py                      # Main Flask app — all API routes
│   ├── auth.py                     # Auth blueprint (signup / login)
│   ├── models.py                   # SQLAlchemy User model
│   ├── quickstart.py               # Google OAuth quickstart helper
│   ├── requirements.txt            # Python dependencies
│   ├── NCCR_Marine_Sample_500.csv  # Marine carbon dataset
│   └── google/
│       ├── gmail.py                # Gmail email count helper
│       ├── drive.py                # Drive storage helper
│       └── youtube.py              # YouTube watch hours helper
└── frontend/
    ├── src/                        # React source code
    ├── index.html
    ├── vite.config.ts
    ├── tailwind.config.ts
    └── package.json
```

---

## 🚦 Getting Started

### Prerequisites
- Python 3.9+
- Node.js 18+ (or Bun)
- A Google Cloud project with Gmail, Drive, and YouTube APIs enabled
- `credentials.json` downloaded from Google Cloud Console (OAuth 2.0 Desktop App)

> **Simulation Mode**: If `credentials.json` is missing, the app runs in simulation mode — all Google API values are simulated and no real data is fetched. Great for local testing without billing.

### 1. Clone the Repository

```bash
git clone https://github.com/AasthaKapoor27/CarbonScopeHackx.git
cd CarbonScopeHackx
```

### 2. Start the Backend

```bash
cd backend

# Create and activate virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Place your credentials.json in the backend/ directory
# Download from: Google Cloud Console → APIs & Services → Credentials

# Run the Flask server
python app.py
```

✅ Backend runs at `http://localhost:5000`

On first run, a browser window will open for Google OAuth. After authentication, a `token.json` is saved automatically for subsequent runs.

### 3. Start the Frontend

```bash
cd frontend

# Install dependencies
npm install       # or: bun install

# Start development server
npm run dev       # or: bun dev
```

✅ Open [http://localhost:5173](http://localhost:5173) 🚀

---

## 🔌 API Reference

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/` | API overview and route listing |
| `GET` | `/api/total_co2` | Total CO₂ for today (email + storage + video) |
| `GET` | `/api/category/pie` | Carbon breakdown by category (for pie chart) |
| `GET` | `/api/weekly/total` | 7-day carbon totals |
| `GET` | `/api/daily_breakdown` | Emails, storage GB, video hours for today |
| `GET` | `/api/carbonchart` | 6-month digital carbon vs. offset data |
| `GET` | `/api/data?page=1&limit=20` | Paginated marine project records |
| `GET` | `/api/data/<id>` | Single marine project record by ID |
| `GET` | `/api/filter?column=X&value=Y` | Filter marine records by column value |
| `GET` | `/api/columns` | List all available dataset columns |
| `POST` | `/api/verify/<project_id>` | Mark a project as verified |
| `POST` | `/api/add` | Add a new marine project (starts as Pending) |
| `POST` | `/execute_plan` | Trigger a Google API action |
| `GET` | `/api/settings` | Get user settings |
| `POST` | `/api/settings/profile` | Update profile settings |
| `POST` | `/api/settings/notifications` | Update notification preferences |
| `POST` | `/api/settings/privacy` | Update privacy settings |
| `POST` | `/signup` | Register a new user |
| `POST` | `/login` | Authenticate a user |

---

## ⚙️ Environment & Configuration

No `.env` file is required by default. Google credentials are handled via `credentials.json` and the auto-generated `token.json`.

For production or custom setups, update the database URI in `app.py`:

```python
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///users.db'
# Replace with PostgreSQL URI for production:
# app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://user:pass@host/dbname'
```

---

## 🗺️ Roadmap

- [ ] PostgreSQL migration for production-ready data persistence
- [ ] OAuth token refresh handling for long-running sessions
- [ ] Per-user carbon history and trend analytics
- [ ] Carbon offset recommendation engine
- [ ] Hosted deployment with managed Google API billing tier

---

## 👩‍💻 Team

| Name |
|------|
| Aastha Kapoor |
| Aarushi Shreevastava |
| Namita Narang |
| Spriha Podder |

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Built with 💚 for [HackX](https://hackx.manipal.edu) — tracking the carbon cost of our digital lives**

*If you found this useful, please ⭐ star the repository!*

</div>
