# 🚨 Aether Link – Resilient Response

**Tagline:** *"Decentralizing Chaos, Centralizing Hope."*

Aether Link is an **offline-first, multi-agency disaster coordination platform** that enables citizens to request emergency help even when the internet is completely unavailable. It provides a web-based landing page for citizens (with map, address search, and SMS simulation) and a separate agency dashboard to view, assign, and resolve incidents. The system uses `localStorage` as a mock database, works entirely offline, and syncs automatically when connectivity returns.

---

## 📌 Features

### Citizen Landing Page (`index.html`)
- ✅ **Interactive Map** (Leaflet + CartoDB Voyager tiles) – clear place labels, click to set location.
- ✅ **Address Search** – geocoding via LocationIQ API (free tier).
- ✅ **Emergency Request Form** – description + priority (Normal/High/Critical).
- ✅ **Offline Submission** – requests saved to `localStorage` and queued in `pendingSync`.
- ✅ **SMS Fallback Simulation** – parse `HELP lat,lng description` and create incident.
- ✅ **Auto/Manual Sync** – when internet returns, offline requests are merged into agency dashboard.
- ✅ **Online/Offline Badge** – shows connection status and pending count.
- ✅ **Toast Notifications** – instant feedback for all actions.

### Agency Dashboard (`dashboard.html`)
- ✅ **Map with Markers** – red for pending incidents, blue for available responders.
- ✅ **Incident List** – view all pending requests with priority badges.
- ✅ **Nearest Responder Assignment** – Haversine distance calculation, ETA display.
- ✅ **Resolve Incidents** – mark as resolved, free up responder.
- ✅ **Sync Pending Requests** – merge offline requests created by citizens.
- ✅ **Real‑time UI Refresh** – no page reload after actions.

### Shared Resilience
- ✅ **No Backend Required** – all data stored in browser `localStorage`.
- ✅ **Zero Infrastructure Cost** – static HTML/CSS/JS, deploy anywhere.
- ✅ **Responsive Design** – works on mobile, tablet, and desktop.
- ✅ **PWA Ready** – can be extended with service worker and manifest.

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|------------|
| Frontend | HTML5, Tailwind CSS, Vanilla JS (ES6+) |
| Mapping | Leaflet.js + CartoDB Voyager tiles |
| Geocoding | LocationIQ API (free tier) |
| Offline Storage | Browser `localStorage` |
| Icons | FontAwesome 6 |
| Version Control | Git + GitHub |

> **No build step, no npm, no backend** – just open the `.html` files.

---

## 📂 Project Structure
aether-link/
├── index.html # Citizen landing page (request form + map + SMS sim)
├── dashboard.html # Agency dashboard (incident list + responder map)
└── README.md

---

## 🔧 Setup & Installation (No Server Required)

1. **Clone or download** the repository.
2. **Open `index.html`** in any modern browser (Chrome, Firefox, Edge, Safari).
3. **Open `dashboard.html`** in another tab or window.
4. *(Optional)* For address search to work, **get a free LocationIQ API key**:
   - Sign up at [locationiq.com](https://locationiq.com/)
   - Copy your API key (starts with `pk.`)
   - In `index.html`, find `const API_KEY = "pk..."` and replace with your key.
5. **Test offline:**  
   - Turn off Wi‑Fi (or use DevTools → Network → Offline).  
   - Submit a request – it saves offline.  
   - Turn Wi‑Fi on – the request automatically syncs to the dashboard.

---

## 🤝 How It Works (Process Flow)

1. **Citizen (online)** → clicks map / searches address → fills description + priority → request saved to `localStorage` → dashboard shows instantly.
2. **Citizen (offline)** → same flow → request saved to `localStorage` + `pendingSync` queue → badge shows "Offline (1 pending)".
3. **SMS fallback (simulated)** → user types `HELP lat,lng description` → system parses → creates incident → stored same way.
4. **Agency dashboard** → loads pending incidents from `localStorage` → click **Assign** → nearest responder calculated (Haversine) → ETA shown → responder marked busy.
5. **Resolve** → incident status changed → removed from list → responder becomes available again.
6. **Sync** → when internet returns, `pendingSync` queue merged into `incidents` → dashboard updates.

---

## 📜 License

This project is open source and available under the **MIT License**.

---

## 👥 Team

**Aether Link** – Built by Team Techelevate

## 🙏 Acknowledgements

- [Leaflet](https://leafletjs.com/) – interactive maps
- [CartoDB](https://carto.com/) – free map tiles
- [LocationIQ](https://locationiq.com/) – geocoding API
- [Tailwind CSS](https://tailwindcss.com/) – rapid UI styling
- [FontAwesome](https://fontawesome.com/) – icons

---

## 🔮 Future Enhancements

- Real SMS gateway integration (Twilio / Fast2SMS)
- Cloud backend (Firebase / Supabase) for multi‑device sync
- AI‑based priority classification from description text
- PWA installation (service worker + manifest)
- Offline map tile caching (Leaflet.Offline)
- Push notifications for responders

---

**Made with ❤️ for disaster resilience.**  
*"When networks fail, help still prevails."*
