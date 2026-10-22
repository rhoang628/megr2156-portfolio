# A2 – Truss Stress Analysis  

## Documentation Quality & Introduction  
Comprehensive technical documentation establishes a transparent engineering baseline, enabling external reviewers to rigorously evaluate the underlying methodology, safety margins, and structural design decisions with confidence.

<div align="center">
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="./System_Overview.png" alt="Truss System Overview" width="385" height="250" style="cursor: pointer;">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Truss Configuration and System Overview Diagram
    </figcaption>
  </figure>
</div>

## Truss Geometry & Static Analysis  
### Geometry & Element Layout  
The overall truss configuration was designed with geometric simplicity to facilitate clear equilibrium calculations while maintaining structural stability. The member lengths were defined as follows: 

### Free Body Diagrams (FBDs)  
<small>***(Clicking on the images will enlarge them)***</small>  
Free body diagrams were sketched and labeled for each individual joint on the truss to isolate external reactions and internal member force interactions. Specifically, the FBD for Node C incorporates 

### Symbolic & Numerical Force Solutions  
Internal forces were solved symbolically across the joint equilibrium equations (e.g., &sum;F<sub>y</sub> = F<sub>BC</sub>&middot;sin(&theta;<sub>1</sub>) + F<sub>CA</sub>&middot;sin(&theta;<sub>2</sub>) + ... )

<div align="center">
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="./Screenshot_33.jpg" alt="Joint FBD Sketches" width="385" height="240" style="cursor: pointer;">
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
*   **Symbolic Solution:** The allowable stress boundary was established by dividing the yield strength by the safety factor (&sigma;<sub>all</sub> = S<sub>y</sub> / SF). Substituting this into the axial stress expression leads to the minimum area requirement.  
*   **Numerical Solution & Weight:** Substituting numerical values results in a minimum cross-sectional area of 0.0001417 m², or 141.7 mm², which satisfies the design objectives within the specified safety margin.

## Connecting Pin Shear Design  
### Structural Pin Parameters  
*   **Knowns & Quantities:** Shear force V = 47.47 kN, tensile yield strength = 170 ksi, shear yield strength &tau;<sub>yield</sub> = 0.5 &times; S<sub>y</sub>, safety factor SF = 4, configured across the pin group.  
*   **Unknowns:** Allowable shear stress &tau;<sub>all</sub> and minimum pin cross-sectional area A<sub>pin</sub>.  
*   **Symbolic & Numerical Area:** The allowable shear stress boundary was formulated as &tau;<sub>all</sub> = (0.5 &times; S<sub>y</sub>) / SF, yielding the symbolic area equation: A<sub>pin</sub> = V / (&tau;<sub>all</sub> &times; n).  
*   **Approximate Weight:** Assuming four pins with an individual length of 50 mm, the total pin volume equates to 3.95 in³. Multiplying by the material density (0.278 lb/in³) results in a combined pin weight of approximately 1.10 lb.

<div align="center">
  <figure style="display: inline-block; margin: 10px; vertical-align: top;">
    <img src="./Screenshot_34.jpg" alt="Pin Shear FBD" width="385" height="230" style="cursor: pointer;">
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 5px;">
      Critical Pin Free Body Diagram and Shear Planes
    </figcaption>
  </figure>
</div>  

## CAD Modeling & Mass Properties Verification  
A 3D parametric model of the truss structure was generated using CAD software. The framework was constructed to track the exact mathematical values calculated during the sizing phase.  

<div align="center">
  <p><small>***(Click on any image to zoom)***</small></p>

  <!-- ROW 1 -->
  <div style="display: block; margin-bottom: 10px;">
    <figure style="display: inline-block; margin: 5px; vertical-align: top; width: 22%;">
      <img src="./Screenshot_35.jpg" alt="CAD Step 1" width="100%" style="cursor: pointer; max-width: 200px; height: auto;">
    </figure>
    <figure style="display: inline-block; margin: 5px; vertical-align: top; width: 22%;">
      <img src="./Screenshot_36.jpg" alt="CAD Step 2" width="100%" style="cursor: pointer; max-width: 200px; height: auto;">
    </figure>
    <figure style="display: inline-block; margin: 5px; vertical-align: top; width: 22%;">
      <img src="./Screenshot_27.jpg" alt="CAD Step 3" width="100%" style="cursor: pointer; max-width: 200px; height: auto;">
    </figure>
    <figure style="display: inline-block; margin: 5px; vertical-align: top; width: 22%;">
      <img src="./Screenshot_26.jpg" alt="CAD Step 4" width="100%" style="cursor: pointer; max-width: 200px; height: auto;">
    </figure>
  </div>

  <!-- ROW 2 -->
  <div style="display: block; margin-bottom: 5px;">
    <figure style="display: inline-block; margin: 5px; vertical-align: top; width: 22%;">
      <img src="./Screenshot_30.jpg" alt="CAD Step 5" width="100%" style="cursor: pointer; max-width: 200px; height: auto;">
    </figure>
    <figure style="display: inline-block; margin: 5px; vertical-align: top; width: 22%;">
      <img src="./Screenshot_31.jpg" alt="CAD Step 6" width="100%" style="cursor: pointer; max-width: 200px; height: auto;">
    </figure>
    <figure style="display: inline-block; margin: 5px; vertical-align: top; width: 22%;">
      <img src="./Screenshot_28.jpg" alt="CAD Step 7" width="100%" style="cursor: pointer; max-width: 200px; height: auto;">
    </figure>
    <figure style="display: inline-block; margin: 5px; vertical-align: top; width: 22%;">
      <img src="./Screenshot_29.jpg" alt="CAD Step 8" width="100%" style="cursor: pointer; max-width: 200px; height: auto;">
    </figure>
  </div>

  <!-- Unified Label for the Grid -->
  <p style="font-size: 0.85em; color: gray; margin-top: 5px; text-align: center;">
    Process from design to assembly
  </p>
</div>

*   The truss framework (excluding connecting hardware) was successfully modeled as a single integrated part file.  
*   Connecting pins were modeled as discrete cylinders matching the calculated cross-sectional areas and an individual length of 50 mm, maintaining exact alignment.  
*   The cross-sectional area of each individual element was strictly preserved at the pin joint intersections to satisfy structural integrity, geometric constraints, and safety margins.  
*   Material density and mass properties were assigned within the CAD environment, enabling automated computation of the predicted total assembly mass and weight.  

## Engineering Lessons Learned  
The design process demonstrated how critical maximum internal force iterations dictate material cross-section selection when applying stringent safety factor thresholds. Balancing analytical stress equations with practical fabrication constraints was essential for producing a robust yet efficient truss design.

<div align="center" style="margin: 25px 0; gap: 12px; display: flex; justify-content: center; flex-wrap: wrap;">
  
  <!-- PDF Report Download Button -->
  <a href="./MEGR%202156.pdf" download="MEGR 2156.pdf" style="
    background-color: #d32f2f; 
    color: white; 
    text-decoration: none;
    padding: 12px 22px; 
    font-size: 0.95em; 
    font-weight: bold; 
    border-radius: 5px; 
    box-shadow: 0 2px 5px rgba(0,0,0,0.15);
    display: inline-block;
    transition: background-color 0.2s;">
    📕 Download Truss Work PDF
  </a>

  <!-- ZIP Archive Download Button -->
  <a href="./A2.zip" download="A2.zip" style="
    background-color: #f57c00; 
    color: white; 
    text-decoration: none;
    padding: 12px 22px; 
    font-size: 0.95em; 
    font-weight: bold; 
    border-radius: 5px; 
    box-shadow: 0 2px 5px rgba(0,0,0,0.15);
    display: inline-block;
    transition: background-color 0.2s;">
    📦 Download CAD File .zip
  </a>

</div>
