# Group Portfolio: Lead Screw Design

## Leadscrew Sizing, Speed, Torque & Flange Nut Selection (Randy Hoang)

For my part of the project, I focused on sizing the leadscrew drivetrain for our $2\text{ kN}$ testing frame. I established our center-to-center span at $150\text{ mm}$ ($5.91\text{ in}$), worked through the minimum root diameter required to handle the axial load safely, found the motor rotational speed range needed to hit our $1\text{--}50\text{ mm/min}$ crosshead travel speeds, calculated the peak input torque per screw, and picked out a matching bronze flange nut ([`97790A110`](https://www.mcmaster.com/97790A110/)) from McMaster-Carr so the rest of the team has the exact mounting dimensions for the crosshead and CAD assembly.

<div align="center" style="margin: 20px 0;">
  <figure style="display: inline-block; width: 100%; max-width: 900px; margin: 0 auto;">
    <iframe src="Leadscrew_Hand_Calculations.pdf" width="100%" height="600px" style="border: 1px solid #ccc; border-radius: 4px;">
      <p>Your browser does not support iframes. 
         <a href="Leadscrew_Hand_Calculations.pdf">Download the Hand Calculations PDF instead.</a>
      </p>
    </iframe>
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 8px;">
      Hand Calculations &amp; Free Body Diagrams
    </figcaption>
  </figure>
</div>

### Component Selection & Design Notes
- **Dual-Screw Span & Load Split ($L_b = 150\text{ mm}$ / $5.91\text{ in}$):** Placing the two identical leadscrews at a $150\text{ mm}$ center-to-center distance keeps the crosshead compact and prevents beam sagging under load. Running them in parallel splits our $2000\text{ N}$ ($2\text{ kN}$) total load evenly to $P = 1000\text{ N}$ ($224.8\text{ lbf}$) per screw, which keeps the crosshead balanced and prevents binding.
- **Leadscrew Size:** Even though axial stress with a safety factor of $4$ only requires a $3.66\text{ mm}$ ($0.144\text{ in}$) root diameter, going with a standard **$1/2^{\prime\prime}-10$ Acme** single-start steel screw gives us plenty of stiffness over the $18\text{-inch}$ minimum height and pairs easily with standard hardware.
- **Why Part [`97790A110`](https://www.mcmaster.com/97790A110/):** A lot of standard bronze flange nuts on McMaster aren't load-rated, so I went with [**97790A110**](https://www.mcmaster.com/97790A110/) (932 Bearing Bronze, Acme Class 2C) because it is explicitly rated for **$1,200\text{ lbf}$ dynamic thrust** and **$35,000\text{ psi}$ tensile strength**. Against our $224.8\text{ lbf}$ load per screw, that gives us a real safety factor of $5.34$.
- **Self-Locking Lead:** The $1/2^{\prime\prime}-10$ single-start profile has a $0.1^{\prime\prime}$ ($2.54\text{ mm}$) lead, meaning the system won't back-drive when the motors stop and only needs $1.26\text{ N}\cdot\text{m}$ of torque per screw at peak load.

<div align="center" style="margin: 20px 0;">
  <figure style="display: inline-block; width: 100%; max-width: 900px; margin: 0 auto;">
    <iframe src="Precision Acme Flange Nut, 1_2_-10 Thread Size _ McMaster-Carr.pdf" width="100%" height="600px" style="border: 1px solid #ccc; border-radius: 4px;">
      <p>Your browser does not support iframes. 
         <a href="Precision Acme Flange Nut, 1_2_-10 Thread Size _ McMaster-Carr.pdf">Download the McMaster-Carr Flange Nut Spec Sheet PDF instead.</a>
      </p>
    </iframe>
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 8px;">
      McMaster-Carr Spec Sheet &amp; Drawing — <a href="https://www.mcmaster.com/97790A110/" target="_blank">Part 97790A110 (932 Bearing Bronze)</a>
    </figcaption>
  </figure>
</div>

---

### Analytical Calculations

1. **Baseline Inputs:**
   - Center-to-center span: $L_b = 150\text{ mm}$ ($5.91\text{ in}$)
   - Total axial load: $P_{\text{total}} = 2000\text{ N}$ $\rightarrow$ Load per screw: $P = 1000\text{ N}$ ($224.8\text{ lbf}$)
   - Safety factor: $n_s = 4$
   - 1060 Steel yield strength: $\sigma_y = 380\text{ MPa}$ ($380 \times 10^6\text{ N/m}^2$)
   - Lead ($1/2^{\prime\prime}-10$ Acme): $L = 0.100\text{ in} = 2.54\text{ mm}$ ($0.00254\text{ m}$)

2. **Minimum Root Diameter ($d_r$):**
   $$\sigma_{\text{allow}} = \frac{\sigma_y}{n_s} = \frac{380\text{ MPa}}{4} = 95\text{ MPa}$$
   $$d_r \ge \sqrt{\frac{4P}{\pi \sigma_{\text{allow}}}} = \sqrt{\frac{4(1000\text{ N})}{\pi (95 \times 10^6\text{ N/m}^2)}} = 0.00366\text{ m} = 3.66\text{ mm} \ (0.144\text{ in})$$

3. **Rotational Speed Range ($N_{\min}$ to $N_{\max}$):**
   $$N_{\min} = \frac{v_{\min}}{L} = \frac{1\text{ mm/min}}{2.54\text{ mm/rev}} = 0.39\text{ rpm}$$
   $$N_{\max} = \frac{v_{\max}}{L} = \frac{50\text{ mm/min}}{2.54\text{ mm/rev}} = 19.69\text{ rpm}$$

4. **Max Input Torque per Screw ($T$):**
   - With mean diameter $d_m = d - \frac{L}{2} = 0.01143\text{ m}$ ($0.450\text{ in}$) and steel-on-bronze friction $f = 0.15$:
   $$T = \frac{P d_m}{2} \left( \frac{L + \pi f d_m}{\pi d_m - f L} \right) = \frac{(1000\text{ N})(0.01143\text{ m})}{2} \left( \frac{0.00254\text{ m} + \pi(0.15)(0.01143\text{ m})}{\pi(0.01143\text{ m}) - (0.15)(0.00254\text{ m})} \right) = \mathbf{1.26\text{ N}\cdot\text{m}} \ (\mathbf{11.15\text{ in}\cdot\text{lbf}})$$

5. **Flange Nut Safety Factor Check:**
   $$n_{s,\text{actual}} = \frac{1200\text{ lbf}}{224.8\text{ lbf}} = 5.34 \ge 4.0$$

---

### Handoff Specs for Crosshead & CAD

| Component | Part & Material | Key Dimensions | Rating | Notes for Crosshead / Assembly |
| :--- | :--- | :--- | :--- | :--- |
| **Leadscrews (x2)** | $1/2^{\prime\prime}-10$ Acme, 1060 Steel | $\varnothing 0.500\text{ in}$ Nominal, $18.0\text{ in}$ Long, $L = 0.100\text{ in}$ ($2.54\text{ mm}$) | Right-Hand, Single-Start, Class 2C | Spaced $L_b = 150\text{ mm}$ ($5.91\text{ in}$) center-to-center |
| **Flange Nuts (x2)** | McMaster [**97790A110**](https://www.mcmaster.com/97790A110/) (932 Bearing Bronze) | Barrel $\varnothing 1.000\text{ in}$, Total Length $1.750\text{ in}$, Flange $\varnothing 2.000\text{ in} \times 0.375\text{ in}$ thick | $1,200\text{ lbf}$ Thrust, $35,000\text{ psi}$ Tensile | Needs $\varnothing 1.000\text{ in}$ clearance hole in crosshead + custom bolt holes in the $2.000\text{ in}$ flange |

---

## Crosshead Design (Noah Nicholson)

<div align="center" style="margin: 20px 0;">
  <figure style="display: inline-block; width: 100%; max-width: 900px; margin: 0 auto;">
    <iframe src="A10CrossheadDesign1.pdf" width="100%" height="600px" style="border: 1px solid #ccc; border-radius: 4px;">
      <p>Your browser does not support iframes. 
         <a href="A10CrossheadDesign1.pdf">Download Crosshead Work.</a>
      </p>
    </iframe>
  </figure>
</div>

### Notes on Work
Given the constraints on the crosshead, I had to find the stress and deflection on the crosshead from the given $2000\text{ N}$ load. I found that the minimum thickness to meet the stress requirement was $12.77\text{ mm}$. However, the deflection analysis stated that the minimum thickness would need to be at least $8.94\text{ mm}$. Since the stress analysis yielded a larger minimum thickness, we found that the minimum thickness needed on the crosshead would be $12.77\text{ mm}$. I rounded this number to $15.00\text{ mm}$ in the rest of my work as shown.

---

## Bill of Materials & Cost Analysis (Atiba Johnson)

| Item # | Qty | Name | Cost / Item | Total Cost | Purchase Link |
| :---: | :---: | :--- | :---: | :---: | :--- |
| 1 | 2 | Precision Acme Lead Screw, 1060/Alloy Steel, 1/2"-10 Thread, 2 ft. Long | $65.24 | $130.48 | [Link](https://www.mcmaster.com/6350K61/) |
| 2 | 2 | Precision Acme Flange Nut, 932 Bearing Bronze, 1/2"-10 Thread | $178.60 | $357.20 | [Link](https://www.mcmaster.com/97790A110/) |
| 3 | 4 | T-Slotted Framing Single Rail, 40 mm x 40 mm, 2 ft. Long | $21.15 | $84.60 | [Link](https://www.mcmaster.com/6575N25/) |
| 4 | 8 | T-Slotted Framing Bracket | $7.06 | $56.48 | [Link](https://www.mcmaster.com/5537T937/) |
| **Total** | | | | **$628.76** | |

---

<div align="center" style="margin: 25px 0; gap: 12px; display: flex; justify-content: center; flex-wrap: wrap;">
  <a href="A10.zip" download="A10.zip" style="
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
    📦 Download All Project Files &amp; Calculations (.zip)
  </a>
</div>

<script>
  MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\\(', '\\)']],
      displayMath: [['$$', '$$'], ['\\[', '\\]']]
    }
  };
</script>
<script id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js">
</script>
