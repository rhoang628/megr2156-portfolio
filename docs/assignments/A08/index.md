# A8: Gearbox Design & CAD Assembly

<small>***(Clicking on the images will enlarge them)***</small>

## 1. Documentation & Intent

The intent of this documentation is to capture the complete mechanical design, mathematical modeling, parametric cavity optimization, bearing stack-up, and assembly mating strategy for the MEGR 2156 Assignment 8 Spur Gearbox. A primary objective of this design iteration was resolving severe internal interference by correcting the housing pocket math from pitch-diameter-based geometry to outside-diameter-based geometry with explicit clearance allowances.

### Design Thought Process & Insights
- **Cavity Clearance Correction:** Sizing internal pockets using pitch diameters caused gear tooth tips ($OD$) to crash directly into the housing walls. Recalculating pockets using the gear Outside Diameters ($OD_1 = 0.34375\text{ in}$, $OD_2 = 0.81250\text{ in}$) plus $0.050\text{ in}$ radial clearance ($0.100\text{ in}$ diametral) eliminated interference while preserving wall thickness.
- **Bearing Stack-Up Strategy:** To minimize rotational friction, four bronze sleeve bearings were integrated. The shorter input bearings (`6391K326`, $0.156\text{ in}$ length) fit completely recessed inside the $0.250\text{ in}$ floor/roof housing walls. The longer output bearings (`6391K132`, $0.500\text{ in}$ length) span through the housing, protruding $0.125\text{ in}$ internally to support the output gear and $0.125\text{ in}$ externally to resist high torque loads.
- **Fastener & Assembly Integrity:** Top housing halves utilize #4 clearance holes ($\varnothing 0.128\text{ in}$) with counterbores for flush screw heads, while bottom housing halves feature #4-40 blind tapped holes ($0.375\text{ in}$ thread depth) for secure enclosure clamp forces.

<div align="center">
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="Screenshot_1.jpg" alt="Input Shaft Modeling and Chamfer Details" width="450">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Input shaft model with $0.015\text{ in} \times 45^\circ$ end chamfers
    </figcaption>
  </figure>
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="Screenshot_2.jpg" alt="Input Shaft Chamfer Property Manager" width="450">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Chamfer feature property manager configuration
    </figcaption>
  </figure>
</div>

<div align="center">
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="Screenshot_3.jpg" alt="Output Shaft Dimensions" width="450">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Output shaft baseline geometry ($\varnothing 0.250\text{ in} \times 1.000\text{ in}$)
    </figcaption>
  </figure>
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="Screenshot_4.jpg" alt="Output Shaft Chamfer Application" width="450">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Applying end chamfers to output shaft geometry
    </figcaption>
  </figure>
</div>

<div align="center">
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="Screenshot_5.jpg" alt="Global Variables Equations Table" width="450">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Parametric equations and global variables table for gear kinematics
    </figcaption>
  </figure>
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="Screenshot_6.jpg" alt="Housing Block Overall Dimensions" width="450">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Housing block baseline dimensions ($1.850\text{ in} \times 1.350\text{ in}$)
    </figcaption>
  </figure>
</div>

---

## 2. Mathematical Modeling & Parametric Equations

To ensure accurate mesh engagement and pocket clearance across all CAD features, the parametric global variables were configured according to standard spur gear formulas:

1. **Gear Ratio:** $24:9$ (2.67:1 speed reduction)
2. **Diametral Pitch ($P_d$):** $32\text{ in}^{-1}$ ($20^\circ$ pressure angle)
3. **Pitch Diameters ($D$):**
   $$D_{\text{pinion}} = \frac{N_1}{P_d} = \frac{9}{32} = 0.28125\text{ in}$$
   $$D_{\text{gear}} = \frac{N_2}{P_d} = \frac{24}{32} = 0.75000\text{ in}$$
4. **Center-to-Center Distance ($C$):**
   $$C = \frac{D_{\text{pinion}} + D_{\text{gear}}}{2} = \frac{0.28125 + 0.75000}{2} = \mathbf{0.515625\text{ in}$$
5. **Outside Diameters ($OD$) & Pocket Sizing ($c = 0.050\text{ in}$):**
   $$OD_{\text{pinion}} = \frac{9 + 2}{32} = 0.34375\text{ in} \longrightarrow \text{Cavity Dia}_1 = 0.34375 + 2(0.050) = \mathbf{0.44375\text{ in}$$
   $$OD_{\text{gear}} = \frac{24 + 2}{32} = 0.81250\text{ in} \longrightarrow \text{Cavity Dia}_2 = 0.81250 + 2(0.050) = \mathbf{0.91250\text{ in}$$

<div align="center">
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="Screenshot_7.jpg" alt="Housing Pocket Cut-Extrude Feature" width="450">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Corrected housing pocket cut-extrude using Outside Diameter geometry
    </figcaption>
  </figure>
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="Screenshot_8.jpg" alt="Bearing Counterbore Features" width="450">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Machining internal bearing counterbores and through-bores
    </figcaption>
  </figure>
</div>

<div align="center">
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="Screenshot_9.jpg" alt="Lower Housing Tapped Holes" width="450">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Lower housing #4-40 blind tapped hole feature setup
    </figcaption>
  </figure>
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="Screenshot_10.jpg" alt="Upper Housing Clearance Holes" width="450">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Upper housing #4 clearance hole counterbore configuration
    </figcaption>
  </figure>
</div>

---

## 3. Component Specification & Interface Table

The primary hardware and housing interfaces are compiled in the master specification table below:

| Component / Subsystem | Part Number / Type | Critical Dimensions | Housing Interface | Placement / Alignment Strategy |
| :--- | :--- | :--- | :--- | :--- |
| **Upper Housing** | Custom Machined / Molded | $1.850\text{ in} \times 1.350\text{ in} \times 0.625\text{ in}$ | Top Split Enclosure | #4 Clearance holes ($\varnothing 0.128\text{ in}$) with $\varnothing 0.220\text{ in}$ C'bores. |
| **Lower Housing** | Custom Machined / Molded | $1.850\text{ in} \times 1.350\text{ in} \times 0.625\text{ in}$ | Bottom Split Base | #4-40 Blind Tapped holes ($0.375\text{ in}$ thread, $0.450\text{ in}$ drill depth). |
| **Input Shaft & Pinion** | Steel / McMaster | $\varnothing 0.125\text{ in} \times 1.000\text{ in}$ ($9\text{T}$, $32P_d$) | `6391K326` Bearings | Concentric to input bore, centered inside $0.750\text{ in}$ total internal cavity. |
| **Output Shaft & Gear** | Steel / McMaster | $\varnothing 0.250\text{ in} \times 1.000\text{ in}$ ($24\text{T}$, $32P_d$) | `6391K132` Bearings | Concentric to output bore, centered at $0.515625\text{ in}$ pitch center distance. |
| **Short Input Bearings** | McMaster `#6391K326` | $0.125\text{ in ID} \times 0.1875\text{ in OD} \times 0.156\text{ in L}$ | Blind Counterbore | Seated flush inside $0.156\text{ in}$ deep housing floor/roof pockets. |
| **Long Output Bearings** | McMaster `#6391K132` | $0.250\text{ in ID} \times 0.3750\text{ in OD} \times 0.500\text{ in L}$ | Through-Bore | Centered with $0.125\text{ in}$ distance mate to exterior face ($0.125\text{ in}$ cavity overhang). |

---

## 4. Technical Troubleshooting & SolidWorks Assembly Validation

During the final CAD assembly phase, initial workspace builds required strict hierarchical mating after inserting the four McMaster-Carr bronze sleeve bearings. However, by the end of the final assembly sequence when applying concentric constraints and motion relationships on the bearings and shafts, SolidWorks experienced recurring fatal software crashes, mate solver cyclic errors, and graphics buffer overflows.

### Assembly Workspace & Crash Narrative
- **Base Component Initialization:** The lower housing (`lower_housing<1>`) was fixed at the origin as the primary anchor.
- **Bearing Mates & Progression:** Concentric mates aligned bearing outer diameters to housing bores, followed by distance mates ($0.125\text{ in}$) to position output bearings.
- **System Instability at the End:** By the end of the process, attempting to rebuild the assembly with fully constrained sleeve bearings and gear meshes triggered fatal memory access violations and application crashes in SolidWorks due to complex surface geometry resolution on imported parts.

<div align="center">
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="Screenshot_11.jpg" alt="Assembly Workspace Initialization" width="450">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Initializing assembly workspace with fixed lower housing base
    </figcaption>
  </figure>
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="Screenshot_12.jpg" alt="Bearing Mate Property Manager and Crash State" width="450">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Applying output bearing mates prior to system crash at the end of assembly
    </figcaption>
  </figure>
</div>

---

## 5. Engineering Reflection & Lessons Learned

### Lessons Learned
- **Outside Diameter vs. Pitch Diameter Clearance:** Sizing internal gear pockets strictly by pitch diameters is a common CAD oversight. Always calculate cavity clearance bounds using the full Outside Diameter ($OD = \frac{N+2}{P_d}$) plus radial tolerance to prevent severe component binding.
- **Bearing Stack-Up Management:** Sleeve bearings longer than the wall thickness must be explicitly constrained using Distance Mates rather than surface coincidences to ensure symmetric load distribution on both sides of the wall.
- **Handling Software Stability & Crashes:** Complex imported fastener and bearing STEP files can overwhelm the SolidWorks mate solver by the end of assembly builds. Simplifying geometry or fixing component references beforehand prevents application crashes.

### Documented Time Spent Log
- **Mathematical Modeling & Cavity Calculations:** 2.0 hours
- **CAD Part Sizing & Feature Modifications:** 3.0 hours
- **Assembly Mating & Bearing Stack-Up Setup:** 2.5 hours
- **Software Troubleshooting & Crash Recovery:** 2.0 hours
- **Portfolio Report Assembly & Image Formatting:** 1.5 hours
- **Actual Total Time (Start to Finish):** **11.0 hours**

<div align="center" style="margin: 25px 0; gap: 12px; display: flex; justify-content: center; flex-wrap: wrap;">

  <!-- Master Download Button for All Assets -->
  <a href="gearbox_portfolio_all_assets.zip" download="gearbox_portfolio_all_assets.zip" style="
    background-color: #1976d2; 
    color: white; 
    text-decoration: none;
    padding: 12px 22px; 
    font-size: 0.95em; 
    font-weight: bold; 
    border-radius: 5px; 
    box-shadow: 0 2px 5px rgba(0,0,0,0.15);
    display: inline-block;
    transition: background-color 0.2s;">
    📦 Download All Gearbox CAD Files & Screenshots (.zip)
  </a>

</div>

## Resources

All design calculations, CAD modeling, and assembly troubleshooting were completed using:

<ul style="list-style-type: circle !important; padding-left: 20px;">
  <li style="list-style-type: circle !important; margin-bottom: 4px;">
    Dassault Systèmes SolidWorks Academic Edition
  </li>
  <li style="list-style-type: circle !important; margin-bottom: 4px;">
    McMaster-Carr CAD Models & Component Library
  </li>
  <li style="list-style-type: circle !important; margin-bottom: 4px;">
    Shigley's Mechanical Engineering Design (Spur Gear & Bearing Standards)
  </li>
</ul>

<script>
    MathJax = {
      tex: {
        inlineMath: [['$', '$'], ['\\(', '\\)']]
      }
    };
  </script>
  <script id="MathJax-script" async
    src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js">
  </script>
