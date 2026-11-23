# Skull Base Playground · Pediatric Bones

An interactive 3D teaching model of a 10-month-old skull base, segmented bone by bone and by developmental part (Matt B). It shows linked axial, coronal and sagittal CT slices, an explode slider, tours for each bone, and a CT volume mode. It works on desktop and phones.

Fully static: plain HTML and WebGL2, no build step and no dependencies. The only external request is Google Fonts.

## Publish on GitHub Pages
1. Create a new repository (e.g. `skull-base-playground-peds`) and upload **all files in this folder** to its root, including the hidden `.nojekyll` file.
2. In the repository, go to **Settings → Pages**. Under **Build and deployment** choose **Deploy from a branch**, then select branch `main` and folder `/ (root)`.
3. After a minute the site will be live at `https://<your-username>.github.io/skull-base-playground-peds/`.

## Run locally
The page loads its data with `fetch`, so opening `index.html` straight from disk won't work. Serve the folder instead:
```
python3 -m http.server 8000
```
then open http://localhost:8000.

## Files
- `index.html`: the whole viewer (code, styles and section text)
- `meshes_lo.txt`: low-detail surfaces for every part, loaded first
- `hi_<id>.txt`: high-detail surfaces, loaded per part on demand
- `ct_XX.jpg`: CT slices packed into image atlases for the slice views and volume rendering
- `labels.b64.txt`: the label volume for the slice overlays

Mesh and label data are gzip-compressed and base64-encoded.

## Controls
- **Desktop:** drag to rotate, right-drag or shift-drag to pan, scroll to zoom, hover to name a part, click to send the slice views to that point. Click a part in the list to isolate it; ⇧/⌘-click toggles it.
- **Phone:** drag to rotate, pinch to zoom, and tap a part in the list to toggle it. Section chips sit under the 3D view.
- The mandible is hidden by default; use the parts list or the Mandible section to show it.

Imaging data are de-identified. Segmentation © Matt B. Please credit when sharing.
