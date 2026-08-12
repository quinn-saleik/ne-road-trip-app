# Northeast Road Trip 2026

Personal project — a full-stack-feeling app (live maps, weather, cross-device sync) built in one HTML file with zero build tooling, for a real trip.

Just a fun personal project for a road trip (Sept 2026): Nashville → Pittsburgh → Vermont/New Hampshire → Maine → Boston → NYC → Princeton → Rehoboth Beach → Baltimore → home. Built to use during the trip.

It's one plain `index.html` file, hosted for free on GitHub Pages. No build step, no npm, nothing to install.

## What's in it

- Day-by-day itinerary with drive times, mileage, and stops
- An actual map of the real driving route (not just straight lines between cities)
- A license plate game (tap the states as you spot them, syncs between phones)
- Per-day bucket lists to check off / add to / delete, also synced
- A rough budget tracker for the trip
- Live weather once we're close enough to the date
- Packing list, road trip games, a "what should we listen to" album picker (with Spotify/Apple Music links), and a podcast list
- Some fun extras on the home screen — countdown, mileage tally, confetti when you hit a milestone

## How it works

Everything's client-side — just HTML/CSS/JS in one file, plus:
- [Leaflet](https://leafletjs.com/) for the map
- Route lines were pulled once from [OSRM](http://project-osrm.org/) and are just baked into the file (no live routing calls)
- [Open-Meteo](https://open-meteo.com/) for weather (free, no API key)
- A tiny [Google Apps Script](./TripSync_AppsScript.gs) + Google Sheet as the "backend" for syncing plates/bucket lists between devices

## Updating it

To make a change: edit `index.html` in any text editor, then re-upload it to this repo (replacing the old one). GitHub Pages picks it up automatically. That's it — no build, no git-fu required.

## Sync setup (if you're forking this)

The plate tracker and bucket lists sync across two phones using a free Google Apps Script backend. To set your own up:

1. Make a blank Google Sheet.
2. Extensions → Apps Script, paste in `TripSync_AppsScript.gs`.
3. Deploy → New deployment → Web app. Execute as **Me**, access **Anyone**.
4. Click through the "unverified app" warning (normal for your own scripts).
5. Copy the `/exec` URL it gives you and drop it into the `SYNC_URL` constant near the top of `index.html`.

If you're just updating the script later: Deploy → Manage deployments → new version → Deploy. Same URL, no need to touch `index.html`.

Nothing here costs money or needs an API key — it's all free/keyless services, held together with duct tape for a one-off trip.
