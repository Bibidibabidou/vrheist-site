# VR Heist — Level Design Site

A small static website documenting the space design for **VR Heist**, a co-located, multi-user VR experience in which a crew of thieves breaks into a museum at night.

Built for the **I.BA_LAB_VR** module (BSc Immersive Technologies) by **Anissah Quraishi** and **Natalia Solin**.

🔗 **Live site:** `https://YOUR-USERNAME.github.io/vrheist-site/`

---

## What's inside

| Page | Path | What it shows |
|---|---|---|
| **Floor plans** | [`/`](index.html) | To-scale top-down plans of all five floors, numbered elements with descriptions, design rules, the tension curve, an assessment-criteria map, asset mapping and Unreal implementation notes. |
| **3D graybox** | [`/3d/`](3d/index.html) | Interactive Three.js graybox of the same layout. Orbit the model, explode the floor stack, isolate single floors, switch to eye-level view, and click numbered pins for details. |

### The five floors

| Floor | Mission | Core idea |
|---|---|---|
| **B1** Underground Hideout | Onboarding + cut the power | Learn every interaction safely, then split-information fuse puzzle |
| **G** Laser Gallery | Get the crew to the security booth | Step over / duck lasers, pressure-plate relay, mirror puzzle, sculpture court |
| **1** Treasure Hall | Steal as much as possible in 3:00 | Loot weights, two-person carry, hide from the guard's flashlight |
| **2** The Vault | Open the vault together | Code fragments, simultaneous key turn, dial + tumbler terminal, weight swap |
| **R** Rooftop Getaway | Escape before the guards break in | Hold the door, fire the zipline, everyone grabs together |

## Design constraints

- Everything happens inside a **6 × 6 m** tracked area (optional 3 × 6 m AR staging area).
- **No personal teleport**, so co-location is preserved. Floors change with a **lift**: when every player is inside the 2 × 2 m car in the NE corner, the doors close and the next floor streams in around the players.
- Target platform: **Unreal Engine 5.8** on **Pico 4 Ultra** with LBE co-location, hand and leg tracking.

## Run locally

The site is plain HTML, CSS and JavaScript, with no build step.

```bash
# from the repo root
python3 -m http.server 8000
# then open http://localhost:8000 and http://localhost:8000/3d/
```

Opening the files directly by double-clicking them usually works too. A local server is more reliable for the 3D page because it uses ES modules.

**Dependencies (loaded from CDNs at runtime):**
- [three.js r160](https://threejs.org/) via jsDelivr: rendering, OrbitControls, CSS2DRenderer
- Google Fonts: Space Grotesk, IBM Plex Mono

## Repository structure

```
.
├── index.html      # 2D floor plans + design document
├── 3d/
│   └── index.html  # interactive 3D graybox
├── README.md
└── .gitignore
```

## Deploying to GitHub Pages

1. Push to the `main` branch.
2. Go to **Settings → Pages → Build and deployment**, set *Deploy from a branch*, then choose `main` and `/ (root)`.
3. Wait 1–2 minutes for the deploy (progress shows under **Actions**).

## Editing the layout

Both pages read the same floor data: a `floors` array of zones, walls, windows, lasers, objects and numbered keys, with coordinates in **metres from the NW corner**.
If you change a floor in one file, copy the same `floors` array into the other so the 2D plans and the 3D model stay in sync.

## Related

- The Unreal Engine project itself lives in the course GitLab (`gitlab.switch.ch`), not in this repository.
- Asset research (Sketchfab models) is listed on the floor plans page, under *Your Sketchfab finds*. Check each model's licence before using it.

## Credits

Design and documentation: Anissah Quraishi & Natalia Solin.
Third-party libraries and fonts belong to their respective authors (three.js, MIT License; fonts, SIL Open Font License).
