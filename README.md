<div align="center">

<img src="https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/Flask-Backend-000000?style=for-the-badge&logo=flask&logoColor=white"/>
<img src="https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black"/>
<img src="https://img.shields.io/badge/TypeScript-5-3178C6?style=for-the-badge&logo=typescript&logoColor=white"/>
<img src="https://img.shields.io/badge/Vite-Build-646CFF?style=for-the-badge&logo=vite&logoColor=white"/>
<img src="https://img.shields.io/badge/Tailwind_CSS-Styling-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white"/>

# 🌊 CarbonScope

### Digital Carbon Tracking • Blue Carbon Registry • Carbon Credits Marketplace • Climate Learning

</div>

---

## 🌐 Demo

| | Link |
|---|---|
| 🎬 **Demo Video** | [Watch on Google Drive](https://drive.google.com/file/d/15MGhlgkW2ATjjL0ZTP2NJRyQtvw_NMYU/view) |

> [!WARNING]
> **This project is not deployed publicly.** It integrates with Google APIs (Gmail, Drive, YouTube Data API v3) which require OAuth credentials and incur billing beyond free-tier limits. To try it, please **run it locally** following the Getting Started steps below — a **Simulation Mode** is available if no credentials are provided.

---

## 🚀 What is This?

**CarbonScope** is a full-stack platform built for **HackX** that unifies four connected sustainability domains into one product:

1. **Personal Digital Carbon Tracker** — estimates CO₂ emissions from everyday digital activity (email, cloud storage, video streaming) via Google API integrations
2. **Blue Carbon Registry** — a geospatial verification system for marine/mangrove ecosystem restoration projects
3. **Carbon Credits Marketplace** — a Web3-enabled marketplace for trading verified carbon credits
4. **Learn** — a gamified climate-education module tying real courses to platform capabilities

---

## ✨ Key Features

### 📊 Dashboard & Activity
| Feature | Description |
|---|---|
| Carbon Footprint KPIs | Monthly footprint, actions automated, Green Points, lifetime CO₂ offset |
| Carbon Footprint Trend | 6-month digital emissions vs. offset chart (Recharts) |
| Activity Timeline | Day-by-day breakdown of automated carbon-saving actions (email batching, storage optimization, video quality adjustment) |
| AI Recommendations | OpenAI-powered suggestions (e.g., Smart Email Scheduling, Cloud File Archiving) tagged by difficulty and quantified CO₂ impact per month |

### 🌊 Blue Carbon Registry
| Feature | Description |
|---|---|
| Geospatial Station Data | 500+ NCCR marine monitoring records across Indian coastal sites (Tuticorin, Mumbai, Goa, Mangalore, Puducherry, etc.), each with lat/long |
| Ecological Metrics | Mangrove cover (ha), pH, salinity, dissolved oxygen, turbidity, biodiversity index, fish count, carbon sequestration rate (tCO₂/ha/yr) |
| Verification Workflow | New submissions start as "Pending"; admins verify via API before data is published |
| Restoration Projects | Aggregate stats — total projects, cumulative carbon offset (tons), communities engaged |
| Submit Project Form | Community members can submit new marine project data for review |

### 🛒 Carbon Credits Marketplace
| Feature | Description |
|---|---|
| Web3 Wallet Integration | Connects a crypto wallet for on-chain-style credit trading |
| Credit Listings | Mangrove Blue Carbon, Rainforest Conservation, Seagrass Restoration, Coastal Wetland credits — each with price/ton, availability, and rating |
| Marketplace Stats | Total volume traded, average price/ton, % verified listings, active listing count |

### 🎓 Learn
| Feature | Description |
|---|---|
| Course Library | 6 courses spanning Beginner → Advanced (Digital Carbon Footprint, Blue Carbon Ecosystems, Carbon Credit Verification, AI-Powered Emission Reduction, Community-Led Restoration, ESG Reporting Standards) |
| Skill Badges | Earned per completed course (Climate Basics, Ocean Guardian, Verification Expert, etc.) |
| Progress Tracking | Badges earned, total learning time |

### 🏆 Gamification
- User level system (e.g., "Level 3 – Automation Master")
- Green Points accumulation
- Unlockable achievement badges with progress bars (First Step, Week Warrior, Automation Master, Carbon Champion, Community Leader, Elite Guardian)

### ⚙️ Settings & Account
- Profile management (name, email, organization)
- Notification preferences (email alerts, carbon reduction alerts, project updates, achievement badges)
- Privacy & Integrations controls
- Data Management — export all data or permanently delete account (GDPR-style)

### 🔒 Authentication
- Signup/login with hashed passwords via Flask-SQLAlchemy + SQLite

---

## 🏗️ Architecture

```text
┌─────────────────────────────────────────────────────────────┐
│                         BROWSER                             │
│                                                             │
│   React 18 + TypeScript + Vite + Tailwind CSS              │
│                                                             │
│   • Dashboard & Activity                                   │
│   • Blue Carbon Registry                                   │
│   • Carbon Credits Marketplace                             │
│   • Learn                                                  │
│   • Settings                                               │
└──────────────────────────────┬──────────────────────────────┘
                               │
                          HTTP / JSON
                               │
                               ▼
┌─────────────────────────────────────────────────────────────┐
│                     FLASK BACKEND                           │
│                                                             │
│   API Routes                                                │
│   • /api/total_co2                                         │
│   • /api/carbonchart                                       │
│   • /api/weekly/total                                      │
│   • /api/data                                               │
│   • /api/verify/<id>                                       │
│   • /api/settings/*                                        │
│   • /execute_plan                                          │
│   • /signup                                                │
│   • /login                                                 │
│                                                             │
│   Database                                                  │
│   • Flask-SQLAlchemy                                       │
│   • SQLite                                                  │
│                                                             │
│   Integrations                                              │
│   • Google OAuth                                            │
│   • Gmail API                                               │
│   • Google Drive API                                       │
│   • YouTube Data API v3                                    │
│   • OpenAI API                                              │
│                                                             │
│   Simulation Mode                                          │
│   • Used when credentials.json is unavailable              │
└───────────────────────┬─────────────────────────────────────┘
                        │
             ┌──────────┼──────────┐
             ▼          ▼          ▼
        ┌────────┐ ┌────────┐ ┌──────────┐
        │ Gmail  │ │ Drive  │ │ YouTube  │
        │  API   │ │  API   │ │   API    │
        └────────┘ └────────┘ └──────────┘
```

### Data Flow

```text
Google APIs
     │
     ▼
Flask Backend
     │
     ├── Digital activity data
     ├── Carbon calculations
     ├── Marine registry data
     └── AI recommendations
              │
              ▼
       React Frontend
              │
              ▼
        User Dashboard
```


---

## 🧩 Tech Stack

### Frontend
- **React 18** — Component-based UI framework
- **TypeScript** — Full type safety across components
- **Vite** — Fast build tool and dev server
- **Tailwind CSS** — Utility-first styling
- **shadcn/ui** — Radix UI primitives
- **Recharts** — Carbon trend and breakdown charts
- **TanStack React Query** — Data fetching and state management
- **React Router DOM v6** — Client-side routing

### Backend
- **Flask** — Python web framework
- **Flask-SQLAlchemy** — ORM + SQLite database
- **Flask-CORS** — Cross-origin support

### Integrations & Data
- **Gmail API**, **Google Drive API**, **YouTube Data API v3** — digital activity tracking
- **OpenAI API** — AI-generated carbon-reduction recommendations
- **NCCR Marine Sample Dataset** — 500-record CSV of marine carbon sequestration projects
- **Web3 wallet connection** — Marketplace credit trading interface

---

## 📁 Project Structure

```text
CarbonScopeHackx/
│
├── backend/
│   ├── app.py
│   │   └── Main Flask application and API routes
│   │
│   ├── auth.py
│   │   └── Signup / login authentication
│   │
│   ├── models.py
│   │   └── SQLAlchemy database models
│   │
│   ├── quickstart.py
│   │   └── Google OAuth setup helper
│   │
│   ├── requirements.txt
│   │   └── Python dependencies
│   │
│   ├── NCCR_Marine_Sample_500.csv
│   │   └── Marine carbon registry dataset
│   │
│   └── google/
│       ├── gmail.py
│       │   └── Gmail activity helper
│       │
│       ├── drive.py
│       │   └── Google Drive storage helper
│       │
│       └── youtube.py
│           └── YouTube watch-time helper
│
├── frontend/
│   ├── src/
│   │   └── React + TypeScript source code
│   │
│   ├── index.html
│   │   └── Frontend entry point
│   │
│   ├── vite.config.ts
│   │   └── Vite configuration
│   │
│   ├── tailwind.config.ts
│   │   └── Tailwind CSS configuration
│   │
│   └── package.json
│       └── Node.js dependencies and scripts
│
├── README.md
│   └── Project documentation
│
└── LICENSE
    └── MIT License
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
git clone [https://github.com/AasthaKapoor27/CarbonScopeHackx.git](https://github.com/AasthaKapoor27/CarbonScopeHackx.git)
cd CarbonScopeHackx
```

### 2. Start the Backend
```bash
cd backend
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate
pip install -r requirements.txt
# Place your credentials.json in the backend/ directory
python app.py
```
✅ Backend runs at `http://localhost:5000`

### 3. Start the Frontend
```bash
cd frontend
npm install   # or: bun install
npm run dev   # or: bun dev
```
✅ Open http://localhost:5173 🚀

---

## 🔌 API Reference

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/` | API overview and route listing |
| `GET` | `/api/total_co2` | Total CO₂ for today (email + storage + video) |
| `GET` | `/api/category/pie` | Carbon breakdown by category |
| `GET` | `/api/weekly/total` | 7-day carbon totals |
| `GET` | `/api/daily_breakdown` | Emails, storage GB, video hours for today |
| `GET` | `/api/carbonchart` | 6-month digital carbon vs. offset data |
| `GET` | `/api/data?page=1&limit=20` | Paginated marine project records |
| `GET` | `/api/data/<id>` | Single marine project record by ID |
| `GET` | `/api/filter?column=X&value=Y` | Filter marine records by column value |
| `GET` | `/api/columns` | List all available dataset columns |
| `POST` | `/api/verify/<project_id>` | Mark a marine project as verified |
| `POST` | `/api/add` | Add a new marine project (starts as Pending) |
| `POST` | `/execute_plan` | Trigger a Google API automation action |
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

- [ ] PostgreSQL (with PostGIS) migration for production-ready, geospatially-indexed data
- [ ] Map-based visualization of marine registry stations (Leaflet/Mapbox)
- [ ] OAuth token refresh handling for long-running sessions
- [ ] Per-user carbon history and trend analytics
- [ ] Formal on-chain smart contract layer for the Marketplace
- [ ] Course-to-capability unlocks in the Learn module
- [ ] Hosted deployment with managed Google API billing tier

---

## 👩‍💻 Team

| Name |
|---|
| Aastha Kapoor |
| Aarushi Shreevastava |
| Namita Narang |
| Spriha Podder |

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<div align="center">
<sub>Built with 💚 for HackX — tracking the carbon cost of our digital lives</sub>

*If you found this useful, please ⭐ star the repository!*
</div>
