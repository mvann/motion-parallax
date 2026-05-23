# motion-parallax

**Built to show how UAPs in videos aren't always moving as fast as they may
seem.** A distant object that barely drifts can streak across a moving
camera's frame purely because the *camera* is moving — that's motion parallax.
This demo lets you fly an observer past a stationary object and watch how
dramatic the apparent motion looks at different zoom levels, even though the
object never actually moves.

A mobile-friendly, single-file 3D demo built with Three.js.

## What you're looking at

Six live views:

- **Four camera POV panes (2×2 grid)** — the same observer view at 1×, 30×,
  300×, and 1000× zoom (clockwise from top-left: 1×, 30×, 1000×, 300×). The
  observer flies along a straight path and its camera always points at the
  object. Watch the object slide across the frame as the observer moves — far
  more dramatically at high zoom.
- **Object cam (bottom-left)** — a camera fixed just above and to the side of
  the object, looking at it. The object stays dead still here no matter what
  the observer does. This is the "it isn't actually moving" reference.
- **Top-down map (bottom-right)** — a plan view: the observer (drawn as the
  selected aircraft), its path, the object, the line of sight, and a
  Google-Maps-style distance scale. The same procedural islands as the 3D
  scene are drawn here so the two views obviously match.

Tap/click any window to make it full-screen; tap again to return.

## Controls

1. **Observer Position** — moves the observer along its 20,000 ft path. The
   aircraft dropdown (F-18 Super Hornet, fighter jet, commercial jet,
   helicopter, UAV, biplane, or manual) auto-flies the observer at that
   vehicle's real cruise speed; touching the slider drops to manual.
2. **Object** — the thing being observed, at its true real-world size: latex
   balloon (1 ft), weather balloon (5 ft, default), bird (6 ft wingspan),
   skydiver (6 ft), hot air balloon (60 ft), or blimp (200 ft).
3. **Balloon height** — the object's altitude (500–13,000 ft).

The observer flies at 25,000 ft; the object sits 10,000 ft out from the
observer's path.

## The ocean

The water is a per-pixel procedural shader (no textures), so it stays crisp at
every zoom level: directional swells + simplex-noise chop with domain warping,
foam on the wave crests, a fake sun glint, and a slow time drift. Islands are a
sparse perlin-noise heightfield, banded tan/gray/green by elevation, composited
into the same ocean surface so there's no z-fighting.

## Run

Serve the directory over HTTP and open `index.html`:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000/
```

Or `npm run serve`.

## GitHub Pages

`.github/workflows/pages.yml` deploys to GitHub Pages on every push to `main`.
First-time setup: **Settings → Pages → Build and deployment → Source →
GitHub Actions**. Deployed at `https://<user>.github.io/motion-parallax/`.

## URL parameters

Deep-link a configuration, e.g.:

```
index.html?vehicle=manual&cam=-5000&bal=9000&obj=blimp
```

- `cam` — observer position in ft (−10,000…10,000); also forces manual mode
- `bal` — object height in ft (500…13,000)
- `vehicle` — `f18` | `fighter` | `commercial` | `helicopter` | `uav` | `biplane` | `manual`
- `obj` — `latex` | `weather` | `bird` | `human` | `hotair` | `blimp`

## Files

- `index.html` — everything: HTML, CSS, and JS in one file.
- `vendor/three.module.min.js` — Three.js, vendored so the demo works offline.
