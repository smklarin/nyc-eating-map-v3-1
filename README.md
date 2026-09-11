# NYC Eating Map — v3.2 Dark Prototype

This is an experimental visual redesign of the family NYC restaurant map. It is intentionally separate from the working v2 site.

## What changed

- Replaced Leaflet/raster tiles with **MapLibre GL JS** and an **OpenFreeMap dark vector style**.
- Dark, GIS-inspired interface designed for iPhone Safari.
- Restaurant markers use glowing category-colored dots with compact expand-on-tap labels, and nearby markers cluster automatically when zoomed out.
- Search, cuisine filters, live location, nearest restaurant, Website/Menu, Apple Maps, Google Maps, and Share are retained.
- Added an optional **3D** button. At close zoom it tilts the map and attempts to render subtle building extrusions from the basemap's building layer.
- Added a **North** button to reset map bearing.
- Includes an iPhone Home Screen icon, web app manifest, and a lightweight service worker for the app shell.

## Put it in a separate GitHub repository

1. Create a new public repository, for example `nyc-eating-map-v3-2`.
2. Upload **all five files from this folder** to the root of the repository:
   - `index.html`
   - `manifest.webmanifest`
   - `sw.js`
   - `icon-180.png`
   - `icon-512.png`
3. In the repository, open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select `main` and `/ (root)`, then save.
6. After GitHub deploys, open the Pages URL on your iPhone in Safari.

## iPhone testing

- Tap **My location** and allow location access.
- Tap a glowing restaurant dot or **Show pin**. Tap a numbered cluster to zoom into that group.
- Test Website/Menu, Apple Maps, and Google Maps.
- Zoom into Midtown or Lower Manhattan, then tap **3D**.
- To install it like an app: Safari → Share → **Add to Home Screen** → Add.

## Notes

The v3.2 prototype loads MapLibre from UNPKG and map data/style from OpenFreeMap, so an internet connection is still required for the map itself. The service worker only provides a lightweight cache of the app shell; it is not an offline NYC map.

The 3D building layer is intentionally experimental because the available building attributes can vary by basemap style. If a browser/style combination cannot expose a compatible building layer, the rest of the map still works normally.
