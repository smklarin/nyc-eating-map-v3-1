# NYC Eating Map — v3.3 Dark Prototype

This is an experimental visual redesign of the family NYC restaurant map. It is intentionally separate from the working v2 site.

## What changed

- Replaced Leaflet/raster tiles with **MapLibre GL JS** and an **OpenFreeMap dark vector style**.
- Dark, GIS-inspired interface designed for iPhone Safari.
- Restaurant markers are native MapLibre circle layers, so they stay locked to their exact map coordinates while panning and zooming. There is no clustering; marker radius scales smoothly with zoom so all locations remain readable when zoomed out.
- Search, cuisine filters, live location, nearest restaurant, Website/Menu, Apple Maps, Google Maps, and Share are retained.
- Added an optional **3D** button. At close zoom it tilts the map and attempts to render subtle building extrusions from the basemap's building layer.
- Added a **North** button to reset map bearing.
- Includes an iPhone Home Screen icon, web app manifest, and a lightweight service worker for the app shell.

## v3.3 interaction changes

- Clustering has been removed entirely.
- Map points now use native MapLibre layers rather than HTML markers.
- Marker size is zoom-dependent: very small at city-wide zooms and progressively larger as you zoom into a neighborhood.
- A selected restaurant gets a halo and native map label.
- Selecting a marker filters the restaurant list to that one location.
- **Show all** or a tap on blank map space clears the selection.

## Put it in a separate GitHub repository

1. Create a new public repository, for example `nyc-eating-map-v3-3`.
2. Upload **all six files from this folder** to the root of the repository:
   - `index.html`
   - `manifest.webmanifest`
   - `sw.js`
   - `icon-180.png`
   - `icon-512.png`
   - `README.md`
3. In the repository, open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select `main` and `/ (root)`, then save.
6. After GitHub deploys, open the Pages URL on your iPhone in Safari.

## iPhone testing

- Tap **My location** and allow location access.
- Tap a restaurant dot to select it. The list immediately changes to that restaurant only; tap **Show all** or blank map space to restore the full list.
- Test Website/Menu, Apple Maps, and Google Maps.
- Zoom into Midtown or Lower Manhattan, then tap **3D**.
- To install it like an app: Safari → Share → **Add to Home Screen** → Add.

## Notes

The v3.3 prototype loads MapLibre from UNPKG and map data/style from OpenFreeMap, so an internet connection is still required for the map itself. The service worker only provides a lightweight cache of the app shell; it is not an offline NYC map.

The 3D building layer is intentionally experimental because the available building attributes can vary by basemap style. If a browser/style combination cannot expose a compatible building layer, the rest of the map still works normally.
