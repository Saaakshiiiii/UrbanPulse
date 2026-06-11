# UrbanPulse

UrbanPulse is a civic issue reporting and management platform that lets citizens report local problems — potholes, water leaks, power outages, garbage collection issues, and more — and automatically routes them to the right municipal department with a severity rating and resolution deadline.

## 🔗 Live Links

- **Live App**: [https://urbanpulsein.netlify.app/](https://urbanpulsein.netlify.app/)
- **Backend API**: [https://urbanpulse-1-xze8.onrender.com](https://urbanpulse-1-xze8.onrender.com)

> Note: the backend is hosted on a free tier and may take 20–30 seconds to wake up on the first request after inactivity.

## Features

- **Citizen Reporting** — Submit an incident with description, location (latitude/longitude), and optional image.
- **AI-Assisted Severity Classification** — Incidents are automatically classified as LOW, MEDIUM, or HIGH based on keyword analysis of the description.
- **Automatic Department Routing** — Issues are routed to the correct department: Fire & Rescue, Water Dept, Power & Energy, Public Works, Sanitation, or General Services.
- **SLA Deadline Calculation** — Each incident is assigned an expected resolution time based on severity and category.
- **Tracking Reference ID** — Citizens get a unique reference ID (e.g., `INC-XXXXXXXX`) to track the status of their report.
- **Admin Dashboard** — View active incidents, resolved cases, SLA breaches, and update incident status in real time.

##  Tech Stack

**Frontend**
- HTML, CSS, JavaScript (vanilla)
- Map integration for location-based reporting

**Backend**
- Python, FastAPI
- Uvicorn (ASGI server)
- In-memory data store for incidents

##  Project Structure

```
UrbanPulse-main/
├── frontend/
│   ├── index.html       # Citizen-facing reporting interface
│   ├── admin.html        # Admin dashboard
│   └── js/
│       ├── api.js        # API communication layer
│       ├── map.js         # Map/location handling
│       └── report.js      # Incident reporting & tracking logic
└── backend/
    ├── requirements.txt
    └── app/
        └── main.py        # FastAPI app — classification, routing, SLA logic
```

##  Running Locally

### Backend
```bash
cd backend
pip install -r requirements.txt
uvicorn app.main:app --reload
```
The API will run at `http://127.0.0.1:8000`.

### Frontend
Open `frontend/index.html` in a browser, or serve the `frontend` folder with any static file server. Update the `API_BASE` constant in `js/api.js`, `js/report.js`, and `admin.html` to point to your local backend URL if needed.

##  How It Works

1. A citizen submits a report describing an issue along with their location.
2. The backend analyzes the description text against keyword sets to determine **severity** (LOW / MEDIUM / HIGH).
3. Based on the content, the system determines the **responsible department** and an **SLA deadline** for resolution.
4. The citizen receives a reference ID to track progress.
5. Admins can view all incidents on the dashboard, monitor SLA breaches, and mark incidents as resolved.

##  What I Learned

- Building a lightweight, rule-based classification system that's fast and easy to deploy without heavy ML dependencies.
- Connecting a separately hosted frontend (Netlify) and backend (Render) — handling CORS, environment-specific API URLs, and deployment configuration (build commands, root directories).
- Debugging real deployment issues: folder structure mismatches between repo and hosting platforms, hardcoded localhost URLs, and dependency management for free-tier hosting limits.
