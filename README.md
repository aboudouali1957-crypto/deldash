# 🚚 DelDash — Delivery Dashboard

🇬🇧 **English** · 🇫🇷 [Français](README.fr.md)

> A web platform for managing and tracking deliveries in real time, with a dedicated dashboard for each role: **Super Admin**, **Dispatcher**, **Delivery Driver** and **Customer**.

**🔗 Live demo: https://aboudouali1957-crypto.github.io/deldash/**

![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![Leaflet](https://img.shields.io/badge/Leaflet-199900?logo=leaflet&logoColor=white)
![Chart.js](https://img.shields.io/badge/Chart.js-FF6384?logo=chartdotjs&logoColor=white)
![PWA](https://img.shields.io/badge/PWA-5A0FC8?logo=pwa&logoColor=white)

---

## 📸 Screenshots

| Login | Super Admin |
|---|---|
| ![Login](screenshots/login.png) | ![Super Admin](screenshots/super-admin.png) |

| Dispatcher | Delivery Driver | Customer |
|---|---|---|
| ![Dispatcher](screenshots/dispatcher.png) | ![Delivery Driver](screenshots/delivery-man.png) | ![Customer](screenshots/customer.png) |

---

## 🔑 Demo accounts

| Role | Email | Password |
|---|---|---|
| Super Admin | `del-admin@deldash.ma` | `admin123` |
| Dispatcher | `m.zahiri@deldash.ma` | `disp456` |
| Delivery Man | `a.jabri@deldash.ma` | `driver9` |
| Customer | `a.benjelloun@email.ma` | `cust5` |

On the login page, pick the role, then enter the matching email and password.

---

## ✨ Features

### 👑 Super Admin
- User management (list, add, edit, delete)
- Analytics dashboard with charts (Chart.js)
- Notification center
- Platform settings

### 🧭 Dispatcher
- Live view of current orders
- Assigning orders to drivers
- Interactive delivery map (Leaflet)

### 🛵 Delivery Driver
- Assigned orders and completed deliveries
- Route map
- **Proof of delivery**: photo taken with the phone camera (`getUserMedia` API) or uploaded image, then the order is marked as delivered

### 📦 Customer
- Real-time order tracking on a map with estimated time of arrival (ETA)
- Order history
- Viewing the proof of delivery
- Notifications

### ⚙️ Cross-cutting
- Role-based login with redirection to the right dashboard
- Responsive interface (collapsible sidebar on mobile)
- Installable app (**PWA**: `manifest.json` + Service Worker for offline caching)

---

## 🛠️ Tech stack

| Area | Technologies |
|---|---|
| Front-end | HTML5, CSS3, JavaScript (ES6+, vanilla, IIFE modules) |
| Maps | Leaflet.js |
| Charts | Chart.js |
| PWA | Web App Manifest, Service Worker (Cache API) |
| Browser APIs | Fetch, localStorage, MediaDevices (camera), FileReader, Canvas |
| Data | JSON files simulating an API (orders, users, vehicles, routes…) |
| Deployment | GitHub Pages |

---

## 📁 Project structure

```
deldash/
├── index.html              # Login page
├── super-admin.html        # Super Admin dashboard
├── dispatcher.html         # Dispatcher dashboard
├── delivery-man.html       # Delivery Driver dashboard
├── customer.html           # Customer dashboard
├── manifest.json           # PWA configuration
├── sw.js                   # Service Worker (offline cache)
├── css/                    # Global styles + one file per role
├── js/
│   ├── auth.js             # Login / logout / session
│   ├── app.js              # Shared initialization and navigation
│   ├── data-loader.js      # Loading the JSON data
│   ├── live-tracking.js    # Real-time tracking (polling) + ETA
│   ├── map-utils.js        # Leaflet helpers
│   ├── route-map.js        # Driver route map
│   ├── driver-assignment.js# Driver assignment
│   ├── delivery-proof.js   # Proof of delivery (camera / upload)
│   ├── analytics.js        # Chart.js charts
│   ├── user-management.js  # User CRUD
│   └── ...                 # Notifications, settings, etc.
├── data/                   # Simulated data (JSON)
├── lib/                    # Leaflet and Chart.js bundled locally
└── screenshots/            # Images used in this README
```

---

## 🚀 Running locally

The project loads JSON files with `fetch`, so it needs a small local server (double-clicking `index.html` is not enough).

```bash
git clone https://github.com/aboudouali1957-crypto/deldash.git
cd deldash

# Option 1: Python
python -m http.server 8000
# then open http://localhost:8000

# Option 2: the "Live Server" extension in VS Code
```

---

## 🐞 Notable bug fixes

- **Charts growing forever**: Chart.js used `maintainAspectRatio: false` without a fixed-height container, so each resize made the canvas taller. Fixed by capping the canvas height.
- **Maps not rendering**: Leaflet maps created inside a hidden tab measured a size of 0. Fixed by triggering a resize whenever the user switches tabs.
- **Invisible customer map**: the map container height was only defined in the dispatcher stylesheet. Moved to the shared stylesheet.
- **Empty "Daily Orders" chart**: the date filter counted back from today instead of from the latest date in the data.

---

## 🧠 What I learned

- Structuring a multi-role application in JavaScript without a framework
- Integrating interactive maps and charts with third-party libraries
- Simulating a REST API with JSON files and `fetch`
- Using browser APIs: camera, local storage, Service Worker
- Deploying a static site with GitHub Pages
- Debugging layout issues caused by hidden elements and responsive charts

---

## 🔭 Possible improvements

- Real back-end (Node.js / Express or Laravel) with a database
- Secure authentication (hashed passwords, JWT)
- Real-time updates with WebSockets instead of polling
- Automated tests

> ℹ️ This project is a front-end demo: data is simulated and authentication happens on the client side.

---

## 👥 Authors

- **Ali Aboudou** — [GitHub](https://github.com/aboudouali1957-crypto)
- **Noureddine Abarhane**
