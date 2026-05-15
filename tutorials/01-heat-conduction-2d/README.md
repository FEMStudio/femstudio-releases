# 01 -- Heat conduction on a 2D plate

Steady-state heat conduction on a 1 m × 1 m steel plate. Dirichlet
boundary conditions on the top and bottom edges; the sides are
insulated (natural BC).

Video walkthrough: <YouTube link>

## Files

| File                        | What it is                                                |
|-----------------------------|-----------------------------------------------------------|
| `heat_sim.sif`                  | Solver Input File — the project definition.               |
| `mesh.grd`                 | ElmerGrid mesh recipe. 10 × 10 quads, split to triangles. |
| `diagrams/problem-setup.png`  | Problem schematic, with all four BCs labelled.            |
| `diagrams/workflow.png`       | Workflow diagram.                             |

## Reproducing the result

ElmerStudio: File → Open → `heat_sim.sif`, then Run.

## Expected answer

With these boundary conditions and no heat source, the temperature
field is `T(x, y) = 100 · (1 − y)` — independent of conductivity.
Sample points to verify against:

| (x, y)      | T   |
|-------------|-----|
| (any, 0.0)  | 100 |
| (any, 0.5)  |  50 |
| (any, 1.0)  |   0 |

Linear triangular elements reproduce this exactly (to machine
precision), so any deviation from these values means the BCs are
wrong.

## Notes

- Material values (Steel AISI 1020) are filled in but don't affect
  this steady-state result. They would matter for a transient run.
- See the video for the mesh-generation walkthrough.