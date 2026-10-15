# Pinfield (OpenStreetMap place finder)

A small web app I made to improve how people search for nearby places on OpenStreetMap.
Live site: (add your GitHub Pages link here)

## Features
- Sign up / log in (users are stored in JSON, see "Data" below)
- Search places inside the part of the map you are looking at
- Quick category buttons (cafe, pharmacy, ATM, park, food)
- Results sorted by distance, list and map markers stay in sync
- Route planner (drive, walk or bike)
- Save places with the heart button (saved inside your user record)
- Loading placeholders, error message with Retry, empty-result message
- Dark mode, works on phone and desktop

## How to run
1. Download the folder.
2. Because it loads JSON files, open it with a local server: `npx serve` or the VS Code "Live Server" extension.
3. Open the link it gives you. Demo login: demo@placefinder.app / demo1234

## Deploy on GitHub Pages
Settings > Pages > Source: Deploy from branch > main > / (root) > Save. Wait a minute and the link appears.

## Data
- `data/users.json` is the starting user file (loaded with fetch).
- New accounts and saved places are written to the browser's localStorage in the same JSON format, because a website running on GitHub Pages can not write to a file on the server.
- The menu has a "Download users.json" button that exports the current data.
- Passwords are hashed with SHA-256 before saving. This is fine for a college project, a real app would need a backend.
- `data/pois.json` is sample places for the offline demo checkbox.

## Design decisions
- Used Leaflet for the map because it is a library, not a framework.
- Search only looks at the visible map area, so results are always nearby.
- Used a debounce on map move so it doesn't spam the API.

## Known issues
- Nominatim (the search API) has rate limits. If it fails, tick "offline demo".
- Login is not real security (no server).
- Offline demo only has 5 places in Bengaluru.
