# MedMap AI — Medical Desert Intelligence

> **Databricks × Accenture Hackathon** · Virtue Foundation

Identify and visualize healthcare "medical deserts" across Ghana using AI-powered analysis, anomaly detection, and interactive mapping.

---

## Quick Start

```bash
# 1. Clone & install
git clone <repo>
cd medmap-ai
npm install

# 2. Configure environment
cp .env.example .env
# Edit .env — set VITE_API_URL to your FastAPI backend

# 3. Run dev server
npm run dev
# → http://localhost:5173

# 4. Build for production
npm run build
```

---

## Tech Stack

| Layer       | Tech                                      |
|-------------|-------------------------------------------|
| UI          | React 18 + Vite                           |
| Styling     | Tailwind CSS (custom design system)       |
| Map         | Leaflet + React-Leaflet + leaflet.heat    |
| HTTP        | Axios (auto-fallback to mock data)        |
| CI          | GitHub Actions                            |

---

## Project Structure

```
src/
  components/
    Map/          # MapView, MapPopup — Leaflet integration
    Chat/         # ChatInterface, ChatBubble, CitationPanel
    Facility/     # FacilityCard — rich detail view
    Anomaly/      # AnomalyBadge, AnomalyPanel
    Planning/     # PlanningWizard — 5-step flow
    Demo/         # DemoPanel — hackathon demo mode
    UI/           # Sidebar, StatsBar, LoadingScreen
  hooks/
    useFacilities.js   # Fetches facilities/anomalies/deserts
    useChat.js         # Chat state management
  data/
    mockData.js        # Ghana facility mock data
  utils/
    api.js             # Axios calls with mock fallback
    helpers.js         # Status logic, formatting, typewriter
  styles/
    index.css          # Tailwind + custom overrides
```

---

## GitHub Workflow

```bash
# Always branch from main
git checkout main && git pull
git checkout -b frontend/<feature-name>

# Commit with clear messages
git commit -m "feat(map): add heatmap layer toggle"

# Open PR → never push directly to main
```

---

## API Endpoints (Backend)

| Method | Endpoint      | Description             |
|--------|---------------|-------------------------|
| GET    | /facilities   | All facility records    |
| GET    | /anomalies    | AI-flagged anomalies    |
| GET    | /deserts      | Desert zone polygons    |
| POST   | /query        | LangGraph agent query   |

If the backend is unavailable, the frontend automatically falls back to `src/data/mockData.js`.

---

## Demo Mode

Click **Demo Mode** in the sidebar to launch the hackathon demo panel with 5 pre-loaded queries:

1. Show all ICU gaps across Ghana
2. Find regions with fewer than 10 doctors
3. Which hospitals are critically overcrowded?
4. Map specialist deserts in Upper East
5. Recommend new facility placements for Northern region

Each query runs through the AI agent with a typewriter response animation, source citations, and reasoning plan display.

---

*Built with ❤️ for the Databricks × Accenture Hackathon · Team MedMap AI*
