# Peaks AR

Mobile web app that overlays nearby mountain peak names, heights and distances on the camera view (PeakVisor-style).

**How it works**
- Position: browser Geolocation; ground altitude from the Open-Meteo elevation (DEM) API since phone GPS altitude is noisy.
- Peaks: OpenStreetMap via the Overpass API (`natural=peak` nodes with `name` + `ele`), cached in localStorage per area.
- Orientation: DeviceOrientation. iOS uses `webkitCompassHeading`; Android uses `deviceorientationabsolute`. Pitch is derived from the rotation matrix.
- Projection: each peak's bearing and elevation angle (with earth-curvature/refraction correction) are mapped onto the camera FOV.

**Usage**
1. Open the site on your phone over HTTPS (camera + sensors require it). Optionally "Add to Home Screen".
2. Tap Start, allow motion, camera and location.
3. ⚙︎ to adjust camera FOV, compass correction, search radius and minimum peak height.

No terrain occlusion: peaks hidden behind closer ridges are still labelled.

**Deploy**: static files, any host. This repo serves from GitHub Pages (`main` branch root).
