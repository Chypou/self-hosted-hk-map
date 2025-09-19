# Self-hosted Hollow Knight Map (Standalone)

This is a standalone, self-hosted map viewer using a local base image and markers extracted from your saved MapGenie HTML (`window.mapData`).

## Quick start

1) Install dependencies (Node 18+, Python 3.9+ recommended)
- Node: https://nodejs.org/
- Python: https://www.python.org/

2) Get local Leaflet (no CDN)
- npm install
- npm run vendor

3) Provide your saved HTML
- Put your saved MapGenie HTML in tools/input.html

4) Extract map data (categories + points)
- npm run extract
- This writes data/mapData.json
- If the HTML contains map dimensions, config.json will be updated automatically

5) Provide a base image
- Option A: If you already have a single high-res map image, place it at assets/map.png and set its pixel width/height in config.json
- Option B (optional): Stitch tiles into one image:
  - Edit scripts/stitch_tiles.py args for your tile template and zoom (see the comment at top)
  - python3 scripts/stitch_tiles.py
  - This will create assets/map.png and update config.json (including pixel offsets if edges are empty/missing)

6) Run locally
- npm start
- Open http://localhost:8080

## Notes

- All assets are local (Leaflet vendor files are downloaded to vendor/leaflet).
- Coordinates use a simple pixel CRS (top-left origin). If you stitched a cropped image, offset is handled via config.json.
- Respect licensing/ToS for any images or tiles you download.