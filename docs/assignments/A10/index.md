## Leadscrew Sizing, Speed, Torque & Flange Nut Selection

For my part of the project, I focused on sizing the leadscrew drivetrain for our $2\text{ kN}$ testing frame. I worked through the minimum root diameter required to handle the axial load safely, found the motor rotational speed range needed to hit our $1\text{--}50\text{ mm/min}$ crosshead travel speeds, calculated the peak input torque per screw, and picked out a matching bronze flange nut ([`97790A110`](https://www.mcmaster.com/97790A110/)) from McMaster-Carr so the rest of the team has the exact mounting dimensions for the crosshead and CAD assembly.

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
- **Splitting the Load:** Since we are running two identical leadscrews in parallel, our $2000\text{ N}$ ($2\text{ kN}$) total load splits evenly to $P = 1000\text{ N}$ ($224.8\text{ lbf}$) per screw, which keeps the crosshead balanced and prevents binding.
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
   - Total axial load: $P_{\text{total}} = 2000\text{ N}$ $\rightarrow$ Load per screw: $P = \mathbf{1000\text{ N}}$ ($\mathbf{224.8\text{ lbf}}$)
   - Safety factor: $n_s = \mathbf{4}$
   - 1060 Steel yield strength: $\sigma_y = 380\text{ MPa}$ ($380 \times 10^6\text{ N/m}^2$)
   - Lead ($1/2^{\prime\prime}-10$ Acme): $L = 0.100\text{ in} = \mathbf{2.54\text{ mm}}$ ($0.00254\text{ m}$)

2. **Minimum Root Diameter ($d_r$):**
   $$\sigma_{\text{allow}} = \frac{\sigma_y}{n_s} = \frac{380\text{ MPa}}{4} = \mathbf{95\text{ MPa}}$$
   $$d_r \ge \sqrt{\frac{4 P}{\pi \sigma_{\text{allow}}}} = \sqrt{\frac{4(1000\text{ N})}{\pi (95 \times 10^6\text{ N/m}^2)}} = \mathbf{0.00366\text{ m}} = \mathbf{3.66\text{ mm}} \ (\mathbf{0.144\text{ in}})$$

3. **Rotational Speed Range ($N_{\min}$ to $N_{\max}$):**
   $$N_{\min} = \frac{v_{\min}}{L} = \frac{1\text{ mm/min}}{2.54\text{ mm/rev}} = \mathbf{0.39\text{ rpm}}$$
   $$N_{\max} = \frac{v_{\max}}{L} = \frac{50\text{ mm/min}}{2.54\text{ mm/rev}} = \mathbf{19.69\text{ rpm}}$$

4. **Max Input Torque per Screw ($T$):**
   - With mean diameter $d_m = d - \frac{L}{2} = \mathbf{0.01143\text{ m}}$ ($0.450\text{ in}$) and steel-on-bronze friction $f = 0.15$:
   $$T = \frac{P d_m}{2} \left( \frac{L + \pi f d_m}{\pi d_m - f L} \right) = \frac{(1000\text{ N})(0.01143\text{ m})}{2} \left( \frac{0.00254\text{ m} + \pi(0.15)(0.01143\text{ m})}{\pi(0.01143\text{ m}) - (0.15)(0.00254\text{ m})} \right) = \mathbf{1.26\text{ N}\cdot\text{m}} \ (\mathbf{11.15\text{ in}\cdot\text{lbf}})$$

5. **Flange Nut Safety Factor Check:**
   $$n_{s,\text{actual}} = \frac{1200\text{ lbf}}{224.8\text{ lbf}} = \mathbf{5.34} \ge 4.0$$

---

### Handoff Specs for Crosshead & CAD

| Component | Part & Material | Key Dimensions | Rating | Notes for Crosshead / Assembly |
| :--- | :--- | :--- | :--- | :--- |
| **Leadscrews (x2)** | $1/2^{\prime\prime}-10$ Acme, 1060 Steel | $\varnothing 0.500\text{ in}$ Nominal, $\ge 18.0\text{ in}$ Long, $L = 0.100\text{ in}$ ($2.54\text{ mm}$) | Right-Hand, Single-Start, Class 2C | Spaced $L_b = 150\text{ mm}$ center-to-center |
| **Flange Nuts (x2)** | McMaster [**97790A110**](https://www.mcmaster.com/97790A110/) (932 Bearing Bronze) | Barrel $\varnothing 1.000\text{ in}$, Total Length $1.750\text{ in}$, Flange $\varnothing 2.000\text{ in} \times 0.375\text{ in}$ thick | $1,200\text{ lbf}$ Thrust, $35,000\text{ psi}$ Tensile | Needs $\varnothing 1.000\text{ in}$ clearance hole in crosshead + custom bolt holes in the $2.000\text{ in}$ flange |

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
