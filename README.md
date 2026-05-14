# conch3d

Interactive 3D mollusc-shell viewer — a port of the six-parameter parametric
surface model from Contreras-Figueroa & Aragón (2023), with live sliders
and presets for every specimen in the paper's Table 1.

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
- Three ornamentation sliders: `n` aperture peaks, `c` rib frequency,
  amplitude
- Whorl-count slider (controls the rendered range of `t`)

## Specimen presets (Table 1)

- **Gastropoda — helicoidal**: *Asperiscala pacis*, *Acteon sullivanae*,
  *Lirularia pedroana*, *Brachysphingus mammilatus*, *Biplica obliqua*
- **Gastropoda — limpets**: *Scelidotoma bella*, *Crepidula adunca*
- **Cephalopoda**: *Oregoniceras siskiyouense*, *Nautilus aff. N. cookanum*,
  *Cleoniceras (Grycia) susukii*, *Shasticrioceras patricki*,
  *Baculites boulei* (orthoconic)
- **Bivalvia**: *Cucullaea morani*, *Glycymerita banosensis*,
  *Indogrammatodon vancouverensis*

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
