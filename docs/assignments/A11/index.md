# Motor Selection Design

## Stepper Motor, Mount Bracket & Shaft Coupling (Randy Hoang)

For my part of the project, I focused on selecting the stepper motor, sizing the NEMA 23 motor mount bracket for bearing stress, and sizing the flexible shaft coupling to transfer torque cleanly to the leadscrew drivetrain. Using the required $1.26\text{ N}\cdot\text{m}$ peak torque per screw and $0.39\text{--}19.69\text{ rpm}$ rotational speed range, I selected a NEMA 23 bipolar hybrid stepper motor ([`6627T161`](https://www.mcmaster.com/6627T161/)), calculated the minimum bracket plate thickness in 6061-T6 aluminum, and verified the torsional shear sizing for our clamp-on flexible beam coupling ([`6208K595`](https://www.mcmaster.com/6208K595/)) so the team has exact mounting and coupling dimensions for CAD and assembly.

<div align="center" style="margin: 20px 0;">
  <figure style="display: inline-block; width: 100%; max-width: 900px; margin: 0 auto;">
    <iframe src="Hand Calc A11.pdf" width="100%" height="600px" style="border: 1px solid #ccc; border-radius: 4px;">
      <p>Your browser does not support iframes. 
         <a href="Hand Calc A11.pdf">Download the Hand Calculations PDF instead.</a>
      </p>
    </iframe>
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 8px;">
      Hand Calculations — Motor Selection, Mount Bracket &amp; Coupler Sizing
    </figcaption>
  </figure>
</div>

### Component Selection & Design Notes
- **Why Part [`6627T161`](https://www.mcmaster.com/6627T161/):** This NEMA 23 bipolar hybrid stepper motor provides $600.4\text{ in}\cdot\text{ozf}$ ($\approx 4.24\text{ N}\cdot\text{m}$) holding torque, $1.8^\circ$ full-step resolution, up to $1,300\text{ rpm}$, and a $1/4^{\prime\prime}$ ($0.2498^{\prime\prime}$) D-profile shaft ($3/4^{\prime\prime}$ long) with $1.86^{\prime\prime}$ bolt hole spacing and $4 \times 0.20^{\prime\prime}$ mounting holes.
- **Motor Mount Bracket Thickness:** For a 6061-T6 aluminum bracket ($\sigma_y = 276\text{ MPa}$, safety factor $n_s = 4$) with a $5\text{ mm}$ ($0.005\text{ m}$) bolt diameter under a $1000\text{ N}$ reference load, allowable bearing stress is $69\text{ MPa}$, giving a minimum bearing thickness of $2.90\text{ mm}$—which I chose as **$6.00\text{ mm}$** for higher rigidity and thread engagement.
- **Why Part [`6208K595`](https://www.mcmaster.com/6208K595/):** Torsional shear analysis on 6061-T6 ($\tau_y = 0.577 \times 276 = 159.3\text{ MPa}$, $\tau_{\text{allow}} = 39.83\text{ MPa}$ at $n_s = 4$) with a $1/2^{\prime\prime}$ ($12.7\text{ mm}$) bore requires at least $14.2\text{ mm}$ OD ($0.75\text{ mm}$ radial wall). Selecting the $1\ 1/4^{\prime\prime}$ ($31.75\text{ mm}$) OD, $2^{\prime\prime}$-long spiral-cut aluminum clamp-on coupling ($1/2^{\prime\prime} \times 1/4^{\prime\prime}$ bores, $115\text{ in}\cdot\text{lbf}$ max torque) provides substantial torque margin and zero-backlash alignment compensation.
- **Axial Clearance Check:** Verify that the motor-to-leadscrew axial spacing accommodates the $3/4^{\prime\prime}$ ($0.75^{\prime\prime}$) motor shaft extension and the $2^{\prime\prime}$ overall coupling length without bottoming out.

<div align="center" style="margin: 20px 0;">
  <figure style="display: inline-block; width: 100%; max-width: 900px; margin: 0 auto;">
    <iframe src="6627T161.pdf" width="100%" height="600px" style="border: 1px solid #ccc; border-radius: 4px;">
      <p>Your browser does not support iframes. 
         <a href="6627T161.pdf">Download the McMaster-Carr Stepper Motor Spec Sheet PDF instead.</a>
      </p>
    </iframe>
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 8px;">
      McMaster-Carr Spec Sheet &amp; Drawing — <a href="https://www.mcmaster.com/6627T161/" target="_blank">Part 6627T161 (NEMA 23 Stepper Motor)</a>
    </figcaption>
  </figure>
</div>

<div align="center" style="margin: 20px 0;">
  <figure style="display: inline-block; width: 100%; max-width: 900px; margin: 0 auto;">
    <iframe src="6208K595.pdf" width="100%" height="600px" style="border: 1px solid #ccc; border-radius: 4px;">
      <p>Your browser does not support iframes. 
         <a href="6208K595.pdf">Download the McMaster-Carr Shaft Coupling Spec Sheet PDF instead.</a>
      </p>
    </iframe>
    <figcaption style="font-size: 0.85em; color: gray; margin-top: 8px;">
      McMaster-Carr Spec Sheet &amp; Drawing — <a href="https://www.mcmaster.com/6208K595/" target="_blank">Part 6208K595 (1/2" x 1/4" Clamp-On Flexible Coupling)</a>
    </figcaption>
  </figure>
</div>

---

### Analytical Calculations

1. **Baseline Inputs:**
   - Required input torque per screw: $T = 1.26\text{ N}\cdot\text{m}$
   - Crosshead travel speed range: $v = 1\text{--}50\text{ mm/min}$ with lead $L = 2.54\text{ mm/rev}$ ($0.100\text{ in/rev}$)
   - Safety factor: $n_s = 4$
   - 6061-T6 Aluminum properties: $\sigma_y = 276\text{ MPa}$, $\tau_y = 0.577 \times 276 = 159.3\text{ MPa}$
   - Mount bolt / bore reference: $d_{\text{bolt}} = 5\text{ mm}$ ($0.005\text{ m}$), coupling inner bore $d_i = 12.7\text{ mm}$ ($0.0127\text{ m}$, $1/2^{\prime\prime}$)

2. **Speed Range & Motor Selection:**
   $$N_{\min} = \frac{1\text{ mm/min}}{2.54\text{ mm/rev}} = 0.39\text{ rpm}, \qquad N_{\max} = \frac{50\text{ mm/min}}{2.54\text{ mm/rev}} = 19.69\text{ rpm}$$
   - Selected motor: McMaster-Carr [**6627T161**](https://www.mcmaster.com/6627T161/) (NEMA 23, $600.4\text{ in}\cdot\text{ozf}$ holding torque, $1.8^\circ$/step, $1/4^{\prime\prime}$ D-shaft).

3. **Motor Mount Bracket Minimum Thickness ($t_{\min}$):**
   $$\sigma_{\text{allow}} = \frac{276\text{ MPa}}{4} = 69\text{ MPa}$$
   $$t_{\min} = \frac{1000\text{ N}}{(0.005\text{ m})(69 \times 10^6\text{ N/m}^2)} = 2.90\text{ mm} \rightarrow \mathbf{6.00\text{ mm}} \text{ (chosen for stiffness &amp; thread depth)}$$

4. **Coupler Torsional Shear & Outer Diameter ($d_{o,\min}$):**
   $$\tau_{\text{allow}} = \frac{159.3\text{ MPa}}{4} = 39.83\text{ MPa}$$
   $$\tau_{\max} = \frac{16 T d_o}{\pi(d_o^4 - d_i^4)} \le 39.83 \times 10^6 \implies d_{o,\min} = \mathbf{14.2\text{ mm}}$$
   $$t_{\text{wall,min}} = \frac{14.2\text{ mm} - 12.7\text{ mm}}{2} = 0.75\text{ mm}$$
   - Selected coupling: McMaster-Carr [**6208K595**](https://www.mcmaster.com/6208K595/) ($1\ 1/4^{\prime\prime}$ / $31.75\text{ mm}$ OD $\ge 14.2\text{ mm}$, $1/2^{\prime\prime} \times 1/4^{\prime\prime}$ bores, $115\text{ in}\cdot\text{lbf}$ max torque).

---

### Handoff Specs for Mount & Coupler CAD

| Component | Part & Material | Key Dimensions | Rating | Notes for Mounting / Assembly |
| :--- | :--- | :--- | :--- | :--- |
| **Stepper Motor** | McMaster [**6627T161**](https://www.mcmaster.com/6627T161/) (NEMA 23 Hybrid Stepper) | $2.25^{\prime\prime}$ face ($1.86^{\prime\prime}$ bolt pattern, $4 \times 0.20^{\prime\prime}$ holes), $4.24^{\prime\prime}$ body length, $\varnothing 0.2498^{\prime\prime}$ ($1/4^{\prime\prime}$) $\times 0.75^{\prime\prime}$ D-shaft | $600.4\text{ in}\cdot\text{ozf}$ holding torque, $1.8^\circ$/step, $1,300\text{ rpm}$ max | $12.5^{\prime\prime}$ leads (4-wire bipolar); check shaft + coupler stackup clearance |
| **Motor Mount Bracket** | 6061-T6 Aluminum Plate | $6.00\text{ mm}$ thickness (exceeds $2.90\text{ mm}$ bearing min), NEMA 23 ($1.86^{\prime\prime}$) hole pattern | $\sigma_y = 276\text{ MPa}$, $\sigma_{\text{allow}} = 69\text{ MPa}$ ($n_s = 4$) | Sized for stiffness and thread/fastener engagement around mount holes |
| **Shaft Coupling** | McMaster [**6208K595**](https://www.mcmaster.com/6208K595/) (Aluminum Spiral Beam, Clamp-On) | $1\ 1/4^{\prime\prime}$ ($31.75\text{ mm}$) OD $\times 2^{\prime\prime}$ overall length, $1/2^{\prime\prime} \times 1/4^{\prime\prime}$ bores, $\#8-32 \times 1/2^{\prime\prime}$ clamp screws | $115\text{ in}\cdot\text{lbf}$ max torque, $10,000\text{ rpm}$ max, $0.015^{\prime\prime}$ parallel / $5^\circ$ angular / $0.01^{\prime\prime}$ axial | Zero backlash; clamps $1/4^{\prime\prime}$ motor shaft to $1/2^{\prime\prime}$ leadscrew |
