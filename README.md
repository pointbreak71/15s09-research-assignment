# 15s09 Research Assignment

Julia + JuMP assignment scaffold for **Optimization of Energy Systems**  
Max Glanville & Andres Garcia Angulo

**Research question:** How should a profit-maximising hyperscaler secure power for a new AI data-centre campus (build onsite generation, accept a curtailable grid connection, wait for firm grid service, or a mix) when it must commit before demand and revenue are known?

## Clone

```bash
git clone https://github.com/pointbreak71/15s09-research-assignment.git
cd 15s09-research-assignment
```

## Open the notebook

1. Install [Julia](https://julialang.org/downloads/) (1.10+ recommended).
2. From this folder, activate the project and instantiate:

```julia
using Pkg
Pkg.activate(".")
Pkg.instantiate()   # JuMP, HiGHS, DataFrames, CSV
```

3. Launch Jupyter with the Julia kernel:

```bash
julia -e 'using Pkg; Pkg.add("IJulia")'
jupyter notebook assignment.ipynb
```

Or open `assignment.ipynb` in VS Code / Cursor with the Julia extension.

### Solvers

**Layer 1** (plain LP) solves with **HiGHS** — no commercial license needed. Run the Layer 1 section near the top of `assignment.ipynb` to see optimal gas capacity $G^*$, the objective, and an hourly summary.

**Gurobi** is optional for later layers. After installing the Optimizer and setting `GUROBI_HOME` / `PATH`:

```julia
julia> using Pkg; Pkg.add("Gurobi")
```

## Push / pull (Max & Andres)

```bash
# pull latest from main
git pull origin main

# after editing
git add -A
git commit -m "Describe your change"
git push origin main
```

Prefer short-lived feature branches if you are working in parallel:

```bash
git checkout -b your-initials/task-a
# ... edit ...
git push -u origin your-initials/task-a
# open a PR into main on GitHub
```

## Repo contents

| File | Role |
|------|------|
| `assignment.ipynb` | Assignment notebook: **Layer 1 LP** + Tasks A–E |
| `Project.toml` | Julia deps (JuMP, HiGHS; Gurobi optional) |
| `.gitignore` | Julia / Jupyter noise |
| `README.md` | This file |

## Source

Problem framing and model sketch come from the course research proposal (*How to commit to capacity when the data center is blind on demand*). Mock parameters in the notebook stand in for real PJM / Nvidia / EIA sources listed in the proposal appendix.
