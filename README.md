
# conch3d

Interactive 3D mollusc-shell viewer — a port of the six-parameter parametric
surface model from Contreras-Figueroa & Aragón (2023), with live sliders
and presets for every specimen in the paper's Table 1.






https://github.com/user-attachments/assets/6fefd416-f2d6-45e1-bd4d-08d07a05dea0

<img width="676" height="624" alt="Screenshot 2026-05-22 at 4 58 48 PM" src="https://github.com/user-attachments/assets/174baa5a-bec2-441a-aabf-8a27a428642d" />

Top Snail

<img width="473" height="555" alt="Screenshot 2026-05-22 at 4 58 08 PM" src="https://github.com/user-attachments/assets/92febba8-d016-4070-b930-60bdfcbae7bb" />

Scallop

<img width="616" height="651" alt="Screenshot 2026-05-22 at 5 04 29 PM" src="https://github.com/user-attachments/assets/1de86fd1-f7c2-4299-93e5-e0a921d296e7" />

Nautilus Fossil

## Paper

> Contreras-Figueroa, G. & Aragón, J. L. (2023).
> *A Mathematical Model for Mollusc Shells Based on Parametric Surfaces and the
> Construction of Theoretical Morphospaces.*
> **Diversity** 15(3), 431. <https://doi.org/10.3390/d15030431>

## Run

Open `index.html` in any modern browser. No build step.

## Controls

- Drag to orbit, scroll to zoom (over the canvas)
- Six principal sliders: `b` whorl expansion, `d` horizontal distance,
  `z` vertical translation, `a` aperture ratio, `φ` aperture tilt,
  `ψ` rotation around the local binormal
- Four ornamentation sliders: `n` aperture peaks, `c` rib frequency,
  amplitude, `k` aperture displacement (bivalve hinge offset, §2.7.3)
- Whorl-count slider (controls the rendered range of `t`)

## Specimen presets

Buttons show common names; hover for the scientific name (Table 1
specimens unless noted).

- **Gastropoda — helicoidal**: Wentletrap (*Asperiscala pacis*),
  Barrel-bubble (*Acteon sullivanae*), Top snail (*Lirularia pedroana*),
  Whelk (*Brachysphingus mammilatus*), Agate snail (*Biplica obliqua*)
- **Gastropoda — limpets**: Keyhole limpet (*Scelidotoma bella*),
  Slipper snail (*Crepidula adunca*)
- **Cephalopoda**: Ammonite (*Oregoniceras siskiyouense*),
  Nautilus (*Nautilus aff. N. cookanum*),
  Ammonite (*Cleoniceras (Grycia) susukii*),
  Heteromorph ammonite (*Shasticrioceras patricki*),
  Baculite / orthocone (*Baculites boulei*)
- **Bivalvia**: Ark clam (*Cucullaea morani*),
  Bittersweet clam (*Glycymerita banosensis*),
  Ark clam (*Indogrammatodon vancouverensis*),
  Scallop (not in Table 1)

## Math

The surface follows equation (12) in the paper:

```
λ(t, θ) = γ(t) + C(t, θ)
γ(t)    = e^{bt} (d sin t,  d cos t,  z)
C(t, θ) = e^{bt} (1 − 1/(t+1)) · R_B(ψ) ·
          [(a sinθ cosφ + cosθ sinφ) N(t)
         + (a sinθ sinφ − cosθ cosφ) B(t)]
```

with the Frenet frame `{T, N, B}` on `γ(t)` defined by eqs. (5)–(7).
Optional ornamentation (eqs. 20–21) is applied as `(1 + amp·sin(nθ))` on the
aperture and `(1 + amp·sin(ct))` on the whole generating curve.

## Credit

Slider/p5.js scaffolding adapted from
[rose3d](https://github.com/ludi317/rose3d).
