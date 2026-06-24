# 🌊 CarbonScope

**CarbonScope** is a full-stack web application built for a hackathon that tracks real-time digital carbon footprints and blue carbon (marine) project data. It connects to your Google account (Gmail, Drive, YouTube) to estimate CO₂ emissions from digital activities, while also providing a verified registry of marine carbon sequestration projects.

---

## ✨ Features

- **Digital Carbon Tracker** — Calculates your daily CO₂ footprint from emails sent, cloud storage used, and video streaming hours via Google APIs
- **Carbon Trend Charts** — Visualizes 6-month digital carbon vs. offset trends using Recharts
- **Weekly Breakdown** — Shows day-by-day carbon totals over the past 7 days
- **Marine Project Registry** — Powered by the NCCR Marine dataset (500 records), with pagination, filtering, and per-project verification
- **Admin Verification Flow** — New projects start as "Pending"; admins can verify them via API
- **Google API Actions** — Enables smart email scheduling, YouTube streaming optimization, and Google Drive file archiving
- **User Authentication** — Signup/login with hashed passwords using Flask-SQLAlchemy + SQLite
- **Settings Panel** — User can update profile, notification preferences, and privacy settings

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18, TypeScript, Vite, Tailwind CSS |
| UI Components | shadcn/ui (Radix UI primitives) |
| Charts | Recharts |
| State / Data Fetching | TanStack React Query |
| Routing | React Router DOM v6 |
| Backend | Python, Flask, Flask-CORS |
| Database | SQLite (via Flask-SQLAlchemy) |
| Google Integration | Gmail API, Drive API, YouTube Data API v3 |
| Data | NCCR Marine Sample Dataset (CSV, 500 records) |
| Package Manager (FE) | Bun / npm |

---

## 📁 Project Structure

```
CarbonScopeHackx/
├── backend/
│   ├── app.py                    # Main Flask app — all API routes
│   ├── auth.py                   # Auth blueprint (signup / login)
│   ├── models.py                 # SQLAlchemy User model
│   ├── quickstart.py             # Google OAuth quickstart helper
│   ├── requirements.txt          # Python dependencies
│   ├── NCCR_Marine_Sample_500.csv  # Marine carbon dataset
│   └── google/
│       ├── gmail.py              # Gmail email count helper
│       ├── drive.py              # Drive storage helper
│       └── youtube.py            # YouTube watch hours helper
└── frontend/
    ├── src/                      # React source code
    ├── index.html
    ├── vite.config.ts
    ├── tailwind.config.ts
    └── package.json
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- Node.js 18+ (or Bun)
- A Google Cloud project with Gmail, Drive, and YouTube APIs enabled
- `credentials.json` downloaded from Google Cloud Console (OAuth 2.0 Desktop App)

---

### Backend Setup

```bash
cd backend

# Create and activate virtual environment
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Place your credentials.json in the backend/ directory
# (Download from Google Cloud Console → APIs & Services → Credentials)

# Run the Flask server
python app.py
```

The backend runs at `http://localhost:5000`.

On first run, a browser window will open for Google OAuth. After authentication, a `token.json` is saved automatically for subsequent runs.

> **Simulation Mode**: If `credentials.json` is missing, the app runs in simulation mode — all Google API values are simulated and no real data is fetched.

---

### Frontend Setup

```bash
cd frontend

# Install dependencies
npm install       # or: bun install

# Start development server
npm run dev       # or: bun dev
```

The frontend runs at `http://localhost:5173` and proxies API calls to the Flask backend.

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

### Example: Add a New Marine Project

```bash
curl -X POST http://localhost:5000/api/add \
  -H "Content-Type: application/json" \
  -d '{
    "Station_ID": "MRN-501",
    "Location": "Sundarbans",
    "Latitude": 21.9497,
    "Longitude": 89.1833,
    "Mangrove_Cover_ha": 120.5,
    "Carbon_Sequestration_tCO2_per_ha_per_year": 8.3,
    "pH": 7.8,
    "Salinity_ppt": 18.2,
    "Dissolved_Oxygen_mg_L": 6.4,
    "Turbidity_NTU": 12.1,
    "Biodiversity_Index": 0.74,
    "Fish_Count": 340,
    "Timestamp": "2025-06-01T10:00:00Z"
  }'
```

---

## ⚙️ Environment & Configuration

No `.env` file is required by default. Google credentials are handled via `credentials.json` and the generated `token.json`.

For production or custom setups, you can update the database URI in `app.py`:

```python
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///users.db'
# Replace with PostgreSQL URI for production:
# app.config['SQLALCHEMY_DATABASE_URI'] = 'postgresql://user:pass@host/dbname'
```

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "feat: add your feature"`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

> Built with 💚 for **HackX** — tracking the carbon cost of our digital lives.
