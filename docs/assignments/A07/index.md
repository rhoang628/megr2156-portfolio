# A7: FEA on Bracket

<small>***(Clicking on the images will enlarge them)***</small>

## 1. Documentation & Intent

The intent of this documentation is to capture the complete finite element analysis (FEA) and structural optimization process for the mounting bracket, extending previous work from Assignments #5 and #6. PTC Creo Simulate was used to drive iterative geometric optimization, ensuring high stiffness, high strength, and lightweight performance under a $600\text{ lbf}$ cantilevered load.

### Design Thought Process & Insights

- **Baseline Evaluation:** Initial structural evaluation of Design I revealed large regions of unused solid material in the upper bracket body.
- **Lightweight Strategy:** Material was selectively removed from lower-stress zones—first by adding parallel horizontal through-holes in the upper blocks (Design II), then by introducing a centralized pill-shaped slot in the lower web (Design III).
- **Geometric Refinement & Lessons Learned:** Early iterations showed that sharp interior corners created severe stress concentrations. Transitioning to smooth rounded fillets and pill-shaped slots reduced peak stresses and improved manufacturability.

![Model properties and AL6061-T6 material assignment](Screenshot_1.jpg){ width="450" }

*Model properties and AL6061-T6 material assignment*

![Material library directory and property verification](Screenshot_2.jpg){ width="450" }

*Material library directory and property verification*

![Applying $0.125\text{ in}$ root fillet to mitigate stress concentration](Screenshot_3.jpg){ width="450" }

*Applying $0.125\text{ in}$ root fillet to mitigate stress concentration*

![Design I baseline mass and volume properties report](design1_mass_properties_report.jpg){ width="450" }

*Design I baseline mass and volume properties report*

---

## 2. Preprocessing & Boundary Conditions

To establish a consistent numerical baseline across all outer loop iterations, identical boundary conditions and material parameters were maintained throughout the study:

1. **Static Stress Analysis:** Linear elastic static stress analysis was performed in PTC Creo Simulate.
2. **Material Definition:** Aluminum 6061-T6 ($S_y = 40{,}000\text{ psi}$, $E = 10 \times 10^6\text{ psi}$, Poisson's ratio $\nu = 0.33$).
3. **Constraints Selection:** Fixed 6-degree-of-freedom constraints were applied to the internal T-slot contact surfaces.
4. **Loading Selection:** A static downward force of $600\text{ lbf}$ was applied to the lower cylindrical loading pin surface.
5. **Mesh Selection & Refinement:** AutoGEM tetrahedral meshing was initialized with default coarse settings and then refined locally using maximum element size controls.

![Fixed boundary constraints applied to internal T-slots](Screenshot_4.jpg){ width="450" }

*Fixed boundary constraints applied to internal T-slots*

![600 lbf static downward force on loading pin](Screenshot_5.jpg){ width="450" }

*$600\text{ lbf}$ static downward force on loading pin*

![Design I initial AutoGEM mesh summary (627 elements)](Screenshot_6.jpg){ width="450" }

*Design I initial AutoGEM mesh summary (627 elements)*

![Executing static analysis design study for Design I](Screenshot_7.jpg){ width="450" }

*Executing static analysis design study for Design I*

---

## 3. Computation & Inner Loop Mesh Convergence

Each outer loop design was subjected to a three-iteration inner loop mesh convergence study. Results were monitored to ensure that maximum stress and global displacement stabilized within acceptable engineering tolerances.

### Inner Loop Convergence Summary

- **Design I (Baseline):** Default mesh yielded $627$ elements, establishing baseline static compliance ($\sigma_{\text{max}} = 1.090 \times 10^6\text{ psi}$ at root fillet; $\delta_{\text{max}} = 1.554\text{ in}$).
- **Design II (Horizontal Through-Holes):** Evaluated using default, intermediate, and fine meshes, converging to max stress of $9.595 \times 10^5\text{ psi}$ and max deflection of $1.553\text{ in}$.
- **Design III (Pill-Shaped Slot Cut):** Evaluated using default, intermediate, and fine meshes, achieving final converged results of $6.572 \times 10^5\text{ psi}$ and $1.573\text{ in}$.

![Design I baseline stress and deflection results](Screenshot_17.jpg){ width="450" }

*Design I baseline stress and deflection results ($1.090 \times 10^6\text{ psi}$)*

![Design II horizontal through-hole sketch](Screenshot_15.jpg){ width="450" }

*Design II horizontal through-hole sketch ($\varnothing 0.75\text{ in}$)*

![Extruding upper parallel through-holes](Screenshot_16.jpg){ width="450" }

*Extruding upper parallel through-holes (remove material)*

![Design II default AutoGEM mesh summary (936 elements)](Screenshot_27.jpg){ width="450" }

*Design II default AutoGEM mesh summary (936 elements)*

![Design II intermediate mesh size control](Screenshot_18.jpg){ width="450" }

*Design II intermediate mesh size control ($0.25\text{ in}$)*

![Design II intermediate mesh summary (799 elements)](Screenshot_19.jpg){ width="450" }

*Design II intermediate mesh summary (799 elements)*

![Design II intermediate stress and deflection](Screenshot_20.jpg){ width="450" }

*Design II intermediate stress and deflection ($6.745 \times 10^5\text{ psi}$)*

![Design II fine mesh size control setup](Screenshot_21.jpg){ width="450" }

*Design II fine mesh size control setup ($0.125\text{ in}$)*

![Design II fine mesh summary (1,518 elements)](Screenshot_22.jpg){ width="450" }

*Design II fine mesh summary (1,518 elements)*

![Design II final converged results](Screenshot_14.jpg){ width="450" }

*Design II final converged results ($9.595 \times 10^5\text{ psi}$)*

![Design II mass properties report](design2_mass_properties_report.jpg){ width="450" }

*Design II mass properties report ($0.3927\text{ lbf}$)*

![Design III pill slot sketch dimensions](Screenshot_23.jpg){ width="450" }

*Design III pill slot sketch dimensions ($1.90\text{ in} \times R0.25\text{ in}$)*

![Design III pill slot extrusion cut](Screenshot_24.jpg){ width="450" }

*Design III pill slot extrusion cut*

![Design III iteration 1 FEA results](Screenshot_25.jpg){ width="450" }

*Design III iteration 1 results ($9.595 \times 10^5\text{ psi}$)*

![Design III mesh control setup](Screenshot_26.jpg){ width="450" }

*Design III mesh control setup*

![Design III iteration 2 FEA results](Screenshot_28.jpg){ width="450" }

*Design III iteration 2 results ($8.456 \times 10^5\text{ psi}$)*

![Design III fine mesh control setup](Screenshot_29.jpg){ width="450" }

*Design III fine mesh control setup ($0.125\text{ in}$)*

![Design III fine mesh summary (1,545 elements)](Screenshot_30.jpg){ width="450" }

*Design III fine mesh summary (1,545 elements)*

![Design III converged FEA results](Screenshot_31.jpg){ width="450" }

*Design III converged finest mesh stress ($6.572 \times 10^5\text{ psi}$)*

![Design III final mass properties report](design3_mass_properties_report.jpg){ width="450" }

*Design III final mass properties report ($0.2804\text{ lbf}$)*

---

## 4. Data Interpretation & Outer Loop Optimization Table

The comparison table below compiles the converged finest-mesh results for all three outer-loop iterations:

| Metric / Parameter | Design I (Baseline) | Design II (Horizontal Holes) | Design III (Pill Slot) |
| :--- | :--- | :--- | :--- |
| **Max Stress and Location** | $1.090 \times 10^6\text{ psi}$<br>*(Lower Root Fillet)* | $9.595 \times 10^5\text{ psi}$<br>*(Lower Root Fillet)* | $\mathbf{6.572 \times 10^5\text{ psi}}$<br>*(Lower Root Fillet)* |
| **Max Deflection and Location** | $1.554\text{ in}$<br>*(Loaded Pin Tip)* | $1.553\text{ in}$<br>*(Loaded Pin Tip)* | $\mathbf{1.573\text{ in}}$<br>*(Loaded Pin Tip)* |
| **Mass / Weight** | $0.4792\text{ lbf}$ | $0.3927\text{ lbf}$ | $\mathbf{0.2804\text{ lbf}}$ |
| **Safety Factor ($FS$)** | $0.0367$ | $0.0417$ | $\mathbf{0.0609}$ |
| **Number of Elements** | $627$ elements | $1,518$ elements | $\mathbf{1,545}$ elements |

---

## 5. Design Optimization & Performance Trade-Offs

1. **Design I to Design II Transition:** Extruding two parallel $\varnothing 0.75\text{ in}$ horizontal through-holes in the upper blocks reduced total bracket weight from $0.4792\text{ lbf}$ to $0.3927\text{ lbf}$, achieving an $18.05\%$ mass reduction with minimal stiffness penalty.
2. **Design II to Design III Transition:** Introducing a centralized pill-shaped slot reduced total weight to $0.2804\text{ lbf}$, creating a cumulative $41.49\%$ mass reduction from the original design.
3. **Stress Mitigation:** The smooth semicircular ends of the pill slot effectively distributed bending loads around the material removal zone and reduced peak stress by $31.5\%$.

---

## 6. Engineering Reflection & Lessons Learned

### Lessons Learned

- **Mesh Discretization & Convergence:** Finite element models exhibit mesh dependency near geometrical stress risers. Refining element size from coarse defaults down to $0.125\text{ in}$ produced more reliable stress predictions.
- **Computational Expense vs. Resolution:** Increased mesh density requires more computation time, so local mesh controls should be concentrated around critical fillets and slots.
- **Geometric Stress Concentration Avoidance:** Sharp interior corners create severe stress concentrations. Smooth circular radii and pill-shaped cutouts helped stabilize load paths.
- **Stiffness vs. Mass Optimization:** Material removal near neutral axes and lower-stressed zones minimized structural compliance penalties while maximizing mass efficiency.

### Documented Time Spent Log

- **CAD Modeling & Feature Adjustments:** 2.5 hours
- **FEA Setup, Preprocessing & Solver Execution:** 3.5 hours
- **Data Logging & Mesh Convergence Calculations:** 1.5 hours
- **Report Assembly & Portfolio Integration:** 1.5 hours
- **Actual Total Time (Start to Finish):** **9.0 hours**

[📦 Download CAD Part Files (Design I, II, III)](design1-3.zip)

---

## Resources

All design, simulation, and documentation work was completed using:

- PTC Creo Parametric & Creo Simulate
- Understanding the Finite Element Method - The Efficient Engineer
- Machinery's Handbook (Standard Structural Design & Material Properties)

<script>
    MathJax = {
      tex: {
        inlineMath: [['$', '$'], ['\\(', '\\)']]
      }
    };
</script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
