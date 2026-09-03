# A2 – Truss Stress Analysis  

## Documentation Quality & Introduction  
Comprehensive technical documentation establishes a transparent engineering baseline, enabling external reviewers to rigorously evaluate the underlying methodology, safety margins, and structural design choices. The portfolio is systematically organized using clear hierarchical headers, explicit mathematical derivations, and structured analytical sections that map directly to the design rubric. The structural parameters for the 5-member planar truss were established to support the specified mechanical loads while adhering to strict geometric, material, and safety constraints.  

<div align="center">
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <a href="System_Overview.png" target="_blank">
      <img src="System_Overview.png" alt="Truss System Overview" width="385" height="250" style="cursor: pointer;">
    </a>
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Truss Configuration and System Overview Diagram
    </figcaption>
  </figure>
</div>  

## Truss Geometry & Static Analysis  
### Geometry & Element Layout  
The overall truss configuration was designed with geometric simplicity to facilitate clear equilibrium calculations while maintaining structural stability. The member lengths were defined as follows: Member AB (top chord, horizontal) = 1.2 m, Member BC = 0.5 m, Member CD (bottom chord, horizontal) = 0.4 m, Member CA (diagonal) = 0.8544 m, and Member AD = 0.5 m. A vertical point load of P = 25 kN pointing upward was applied at Node C.

### Free Body Diagrams (FBDs)  
<small>***(Clicking on the images will enlarge them)***</small>  
Free body diagrams were sketched and labeled for each individual joint on the truss to isolate external reactions and internal member force interactions. Specifically, the FBD for Node C incorporates the upward 25 kN load, the vertical force component from Member BC, the horizontal force component from Member CD, and the diagonal force vector from Member CA acting at an angle of 20.56&deg;.

### Symbolic & Numerical Force Solutions  
Internal forces were solved symbolically across the joint equilibrium equations (e.g., &sum;F<sub>y</sub> = F<sub>BC</sub>&middot;sin(&theta;<sub>1</sub>) + F<sub>CA</sub>&middot;sin(&theta;<sub>2</sub>) + P = 0). Numerically solving the equations yielded the internal forces for all structural members, identifying member CA as experiencing the maximum internal compressive force of F<sub>max</sub> = 47.47 kN.  

<div align="center">
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <a href="Joint_FBD_Sketches.jpg" target="_blank">
      <img src="Joint_FBD_Sketches.jpg" alt="Joint FBD Sketches" width="385" height="240" style="cursor: pointer;">
    </a>
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Free Body Diagrams and Equilibrium Framework for Node C
    </figcaption>
  </figure>
</div>  

## Truss Member Sizing  
### Calculations and Allowable Stress  
To determine the safety boundaries, hand calculations were performed to track known constraints against structural geometric requirements.  

*   **Knowns:** Maximum internal force F<sub>max</sub> = 47.47 kN, material yield strength S<sub>y</sub> = 170 ksi (1172 MPa), and a safety factor SF = 3.5.  
*   **Unknowns:** Allowable stress &sigma;<sub>all</sub> and minimum required cross-sectional area A<sub>req</sub>.  
*   **Symbolic Solution:** The allowable stress boundary was established by dividing the yield strength by the safety factor (&sigma;<sub>all</sub> = S<sub>y</sub> / SF). Substituting this into the axial stress relation (&sigma; = F / A) yields the symbolic equation: A<sub>req</sub> = (F<sub>max</sub> &times; SF) / S<sub>y</sub>  
*   **Numerical Solution & Weight:** Substituting numerical values (A<sub>req</sub> = (47,470 N &times; 3.5) / 1,172,109,200 N/m²) results in a minimum cross-sectional area of 0.0001417 m², or 141.7 mm². Utilizing the total cumulative member length of 3.4544 m (3454.4 mm) and a material density of 0.278 lb/in³, the total approximate weight of the truss structure is 8.30 lbs.  

## Connecting Pin Shear Design  
### Structural Pin Parameters  
*   **Knowns & Quantities:** Shear force V = 47.47 kN, tensile yield strength = 170 ksi, shear yield strength &tau;<sub>yield</sub> = 0.5 &times; S<sub>y</sub>, safety factor SF = 4, configured across a single shear connection using 4 pins.  
*   **Unknowns:** Allowable shear stress &tau;<sub>all</sub> and minimum pin cross-sectional area A<sub>pin</sub>.  
*   **Symbolic & Numerical Area:** The allowable shear stress boundary was formulated as &tau;<sub>all</sub> = (0.5 &times; S<sub>y</sub>) / SF, yielding the symbolic area equation: A<sub>pin</sub> = (V &times; SF) / (0.5 &times; S<sub>y</sub>). Evaluating this numerically (A<sub>pin</sub> = (47,470 N &times; 4) / [0.5 &times; 1,172,109,200 N/m²]) gives 324.0 mm², matching a calculated pin diameter of roughly 20.3 mm.  
*   **Approximate Weight:** Assuming four pins with an individual length of 50 mm, the total pin volume equates to 3.95 in³. Multiplying by the material density (0.278 lb/in³) results in a combined pin weight of 1.10 lbs.  

<div align="center">
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <a href="Pin_Shear_FBD.jpg" target="_blank">
      <img src="Pin_Shear_FBD.jpg" alt="Pin Shear FBD" width="385" height="230" style="cursor: pointer;">
    </a>
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Critical Pin Free Body Diagram and Shear Planes
    </figcaption>
  </figure>
</div>  

## CAD Modeling & Mass Properties Verification  
A 3D parametric model of the truss structure was generated using CAD software. The framework was constructed to track the exact mathematical values calculated during the sizing phase.  

<div align="center">

  <!-- Left Screenshot Container -->
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <a href="CAD_Assembly_Rendering.jpg" target="_blank">
      <img src="CAD_Assembly_Rendering.jpg" alt="CAD Assembly Rendering" width="419" height="280" style="cursor: pointer;">
    </a>
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Parametric CAD Assembly Isometric View
    </figcaption>
  </figure>

  <!-- Right Screenshot Container -->
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <a href="CAD_Mass_Props.jpg" target="_blank">
      <img src="CAD_Mass_Props.jpg" alt="CAD Mass Properties Verification" width="419" height="280" style="cursor: pointer;">
    </a>
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Mass Properties and Weight Verification Window
    </figcaption>
  </figure>

</div>  

*   The truss framework (excluding connecting hardware) was successfully modeled as a single integrated part file.  
*   Connecting pins were modeled as discrete cylinders matching the calculated cross-sectional areas and an individual length of 50 mm, maintaining exact alignment.  
*   The cross-sectional area of each individual element was strictly preserved at the pin joint intersections to satisfy structural integrity, geometric constraints, and safety margins.  
*   Material density and mass properties were assigned within the CAD environment, enabling automated computation of the predicted total assembly mass and weight.  

## Engineering Lessons Learned  
The design process demonstrated how critical maximum internal force iterations dictate material cross-section selection when applying stringent safety factor thresholds. Balancing analytical stress equations with manufacturing constraints highlighted the necessity of accounting for single-shear stress concentrations early in the spatial layout phase. Furthermore, integrating hand calculations with parametric 3D CAD modeling verified that maintaining consistent cross-sectional areas at pin joint intersections prevents localized geometric interference while preserving structural stability. Accurately translating material yield limits into allowable stress boundaries ensures that structural components withstand operational loading conditions without experiencing premature failure or excessive weight penalties.  

## Resources   

All reference materials and CAD files used for this portfolio piece:    

<ul style="list-style-type: circle !important; padding-left: 20px;">
  <li style="list-style-type: circle !important; margin-bottom: 4px;">
    <a href="Planar_Truss_System.asm" download>Planar_Truss_System.asm (CAD Assembly File)</a>
  </li>
  <li style="list-style-type: circle !important; margin-bottom: 4px;">
    <a href="Truss_Calculations_Spreadsheet.xlsx" download>Truss_Calculations_Spreadsheet.xlsx (Analytical Model)</a>
  </li>
</ul>

