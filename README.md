# motion-parallax

A mobile-friendly 3D demo of motion parallax.

Two views stacked vertically:

- **Camera POV:** A 3D scene rendered with Three.js. A red hot-air balloon
  hovers in front of a 10,000-ft mountain range. The camera flies along a path
  parallel to the range at 10,000 ft elevation and always points at the balloon.
- **Zoomed (balloon-locked):** Same camera pose, but the FOV is recomputed on
  every frame so the balloon's diameter takes up half the view height. This
  isolates the parallax: the balloon stays put, the mountains slide behind it.
- **Top-down map:** A schematic showing the camera, its path, the balloon, the
  balloon's path, the sight line, and the mountain range.

Two sliders at the bottom:

1. **Camera position** — moves the camera along its path (−10,000 ft to +10,000 ft).
2. **Balloon distance** — moves the balloon perpendicular to the camera's path,
   from the middle of the scene (10,000 ft away from each side) to almost
   touching the mountain base.

Move the camera slider with the balloon near the middle to see strong parallax
(the balloon sweeps the view much faster than the distant mountains). Push the
balloon toward the mountains and the parallax of the balloon vs the mountains
collapses — that's the whole point.

## Run

Just serve the directory over HTTP and open `index.html`:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/
```

Or `npm run serve`.

## GitHub Pages

A workflow in `.github/workflows/pages.yml` deploys this site to GitHub Pages
on every push to `main` (or the active dev branch). First-time setup:

1. Go to **Settings → Pages**
2. Under **Build and deployment → Source**, choose **GitHub Actions**
3. Push (or re-run the workflow from the Actions tab). The deployed URL will
   be `https://<user>.github.io/motion-parallax/`.

## URL parameters

You can deep-link a configuration:

```
index.html?cam=-5000&bal=18000
```

## Files

- `index.html` — everything: HTML, CSS, and JS in one file.
- `vendor/three.module.min.js` — Three.js, vendored so the demo works offline.
