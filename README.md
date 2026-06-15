# My Project — 3D Viewer

Interactive 3D viewer for the **My Project** model, rebuilt from the same template as `ld-villa-3d`.

- **index.html** — three.js viewer (orbit / zoom / pan / fullscreen), streams and decompresses `model.glb.gz`.
- **converter.html** — in-browser Rhino-to-GLB converter (runs locally, nothing uploaded). Drop a `.3dm` file and it produces the compressed `model.glb.gz`.
- **model.glb.gz** — web-optimized, gzipped GLB model. *(add your own file here)*

## Make it yours

Everything is controlled by a small `CONFIG` block near the top of each file's `<script>`:

```js
const CONFIG = {
  PROJECT_NAME: 'My Project',     // index.html — shown in the title + loading screen
  MODEL_FILE:   'model.glb.gz'    // index.html — the gzipped GLB next to it
};
```

`converter.html` has a matching block (`PROJECT_NAME` + `OUTPUT_FILE`) — keep `OUTPUT_FILE` equal to `MODEL_FILE` so the viewer finds the model the converter produces.

## Add your model

1. If you have a Rhino `.3dm`: open `converter.html` in a browser, drag your file in, and it downloads `model.glb.gz`.
2. If you already have a `.glb`: gzip it as `model.glb.gz` (e.g. `gzip -k model.glb`), or switch the loader in `index.html` to load a plain `.glb`.
3. Put `model.glb.gz` next to `index.html` and open `index.html`.

## Run locally

Because the viewer fetches the model file, serve the folder over HTTP rather than opening the file directly:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

## Hosting

Push the folder to a GitHub repo and enable GitHub Pages, or drop it on any static host. No build step required.
