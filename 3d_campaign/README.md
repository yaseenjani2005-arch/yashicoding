# Independent 3-D conjugate campaign - execution package

## Status

**NOT EXECUTED.** No temperature, pressure, residual, mesh-convergence or field result in this folder is a CFD result. The current runtime has no working Gmsh shared library and no installed OpenFOAM/Fluent/COMSOL/STAR-CCM+ conjugate solver.

## Frozen scope

The case matrix contains the six prespecified validation cases and four engineering designs selected before 3-D evaluation. The same material properties, inlet definitions, heat-generation history and 1080 s duration must be used for every case. No case-specific heat-transfer or wetted-area parameter may be tuned after inspecting results.

## Required execution sequence

1. Install an independently maintained conjugate solver and official Gmsh SDK.
2. Generate coarse, medium and fine meshes for D6 Re=300 and 500.
3. Run the time-step matrix for D6 Re=100 and 500.
4. Freeze solver settings after verification.
5. Run all six validation cases and the four engineering-design cases.
6. Populate `results_schema.csv` and archive raw residuals, fields and logs.
7. Calculate GCI/time uncertainty before comparing with axial FVM or POD outputs.

## Minimum acceptance checks

- Global mass imbalance below the prespecified solver tolerance.
- Global energy imbalance reported for every case.
- Iterative residual histories archived, not only final values.
- Mesh and time uncertainty smaller than the claimed model-to-model difference.
- Branch-flow distributions and pressure drop reported.
- D6 Reynolds-number trend and D1-D7 geometry trend evaluated without case-specific tuning.

## Four design verification rule

The high-cooling, balanced, low-power and near-boundary designs are frozen in `campaign_cases.csv`. Their 3-D rankings must be reported even if they disagree with the axial FVM. A ranking reversal is a result, not a reason to retune the reduced model.
