# 02 — Anatomy of a SIF file

A walk through `heat_sim.sif` from Episode 1, section by section.
Reuses that project deliberately — the physics is already familiar,
so the focus is on what each section of the file means and how the
sections connect to each other.

Video walkthrough: https://youtu.be/Zy1-4LNW8oA

## Files

| File | What it is |
|-------------------------------|------------------------------------------------------------|
| `heat_sim.sif` | Same SIF as Episode 1. The subject of the walkthrough. |
| `mesh/` | Same mesh as Episode 1. Included so the SIF runs as-is. |
| `diagrams/sif_anatomy.png` | Reference diagram: how the SIF's sections connect. |

## The twelve sections in this file

| Section | Role |
|---------------------------|----------------------------------------------------------------|
| `Header` | Where the mesh lives; keyword-checking mode. |
| `Simulation` | Steady state vs transient, coordinate system, output frequency.|
| `Constants` | Simulation-wide physical constants (Stefan-Boltzmann etc.). |
| `Solver 1` | The heat solver — physics module + linear-solver settings. |
| `Solver 2` | Result Output — writes `case0001.vtu`. |
| `Body 1` | Binds `Equation`, `Material`, `Body Force`, `Initial Condition` to a mesh region. |
| `Equation 1` | Which solvers are active on the bodies that reference it. |
| `Material 1` | Steel AISI 1020 — density, conductivity, etc. |
| `Body Force 1` | Empty stub. Optional section; left in by the template. |
| `Initial Condition 1` | Empty stub. Optional section; left in by the template. |
| `Boundary Condition 1` | Top edge (mesh boundary 3): `Temperature = 0`. |
| `Boundary Condition 2` | Bottom edge (mesh boundary 1): `Temperature = 100`. |

## How the sections connect

See `diagrams/sif_anatomy.png`. Three groups on the left side of the
SIF — whole-run settings, numbered definitions, and bindings — feed into a single mesh region on the right.

Two structural points worth knowing without watching the video:

- **Body 1 is the keystone.** Numbered definitions (`Solver`,
  `Equation`, `Material`, `Body Force`, `Initial Condition`) sit
  declared in space. None of them does anything until a `Body` block
  references them.
- **Silence is a boundary condition.** The mesh has four boundary
  IDs but only two are referenced by `Boundary Condition` blocks. The
  other two get the natural BC by default — for heat conduction,
  zero flux (insulated).

## Reproducing the result

ElmerStudio: File → Open → `heat_sim.sif`, then Run. The expected
result is the same as Episode 1: a linear gradient `T(y) = 100·(1−y)`,
with `T = 50` at the mid-plate.

## Notes

- The Stefan-Boltzmann constant in `Constants` is unused in this problem — no radiation BC references it — and harmless to leave in.
- `Density` is mandatory in any `Material` block, even when the active physics doesn't reference it. The solver checks for it on parse.
- `Steady State Max Iterations = 1` is correct here because heat conduction with a constant conductivity is linear and there's a
  single physics; one outer iteration suffices.
- For the full keyword reference, see the *ElmerSolver Manual*: <http://www.elmerfem.org/blog/documentation/>