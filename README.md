# motion-parallax

A mobile-friendly 3D demo of motion parallax.

Two views stacked vertically:

- **Camera POV:** A 3D scene rendered with Three.js. A red hot-air balloon
  hovers over the open ocean 10,000 ft out from an observer flying along a path
  at 10,000 ft elevation. The observer's camera always points at the balloon.
- **Zoomed (balloon-locked):** Same camera pose, but the FOV is recomputed on
  every frame so the balloon's diameter takes up half the view height. This
  isolates the parallax: the balloon stays put, the horizon slides behind it.
- **Top-down map:** A schematic showing the observer (as a vehicle icon), its
  path, the balloon, and the sight line.

Controls at the bottom:

1. **Observer Position** — moves the observer along its path (−10,000 ft to
   +10,000 ft). An aircraft dropdown picks the vehicle (fighter, commercial,
   helicopter, UAV, biplane, or manual) and auto-animates the position at the
   chosen cruise speed; touching the slider drops to manual.
2. **Balloon height** — sets the balloon's altitude (500 ft to 15,000 ft).

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
