# Desk Dashboard

A single-file web dashboard for an always-on Android desk display. Shows a live clock, weather, and Google Calendar events in a dark landscape layout.

## Live Demo

> After enabling GitHub Pages: `https://prashanthmoni.github.io/desk-dashboard/`

---

## Setup

### 1. Google Calendar API

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project (e.g. "Desk Dashboard")
3. Enable **Google Calendar API** (APIs & Services → Library)
4. Go to **APIs & Services → Credentials → Create Credentials → OAuth 2.0 Client ID**
   - Application type: **Web application**
   - Authorized JavaScript origins: `https://prashanthmoni.github.io`
   - Authorized redirect URIs: `https://prashanthmoni.github.io`
5. Copy the **Client ID** (looks like `123456789-abc.apps.googleusercontent.com`)
6. Open `index.html`, find the `CONFIG` block at the top, and replace:
   ```js
   GOOGLE_CLIENT_ID: 'YOUR_CLIENT_ID_HERE.apps.googleusercontent.com',
   ```

### 2. Weather Location (optional)

By default the dashboard uses browser geolocation. To hardcode a location, edit the config:

```js
LATITUDE:  37.7749,   // San Francisco example
LONGITUDE: -122.4194,
```

### 3. Other Config Options

```js
TEMP_UNIT:           'fahrenheit',  // or 'celsius'
TIME_FORMAT:         '12h',         // or '24h'
CALENDAR_DAYS_AHEAD: 3,             // days of events to show
```

### 4. Deploy to GitHub Pages

1. Push `index.html` and `README.md` to this repo
2. Go to **Settings → Pages → Source: Deploy from branch → main / root**
3. Your dashboard will be live at `https://prashanthmoni.github.io/desk-dashboard/`

---

## Android Setup

### Option A: Fully Kiosk Browser (Recommended)

1. Install **Fully Kiosk Browser** from Google Play (free version works)
2. Set Start URL to your GitHub Pages URL
3. Enable:
   - Keep Screen On: **ON**
   - Autostart on Boot: **ON**
   - Hide Status Bar: **ON**
   - Hide Navigation Bar: **ON**
   - Screen Orientation: **Landscape**
   - Auto-reload on network reconnect: **ON**

### Option B: Chrome

1. Open Chrome and navigate to your dashboard URL
2. Tap menu → **Add to Home screen** (launches as fullscreen)
3. Install **Stay Alive** or **Keep Screen On** app

### General Tips

- Enable Developer Options → **Stay Awake** (screen stays on while charging)
- Set screen brightness to ~30–40% for always-on use
- Disable notifications from all apps to prevent popups

---

## File Structure

```
desk-dashboard/
├── index.html   # Entire dashboard — single self-contained file
└── README.md    # This file
```

---

## Tech Stack

- Vanilla JavaScript (ES6+), no frameworks, no build step
- [Open-Meteo API](https://open-meteo.com/) — free weather, no API key
- [Google Calendar API v3](https://developers.google.com/calendar) + Google Identity Services
- Hosted on GitHub Pages (free static hosting)
