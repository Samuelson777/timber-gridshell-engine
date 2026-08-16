# Enterprise Timber Gridshell Computational Engine

**By** : SAMUELSON G

A high-performance, WebGL-accelerated computational engine for the parametric generation and real-time structural analysis of timber gridshells. This tool bridges conceptual architectural form-finding with rigorous Eurocode 5 (EC5) structural engineering, providing instant visual and quantitative feedback on ultimate limit state (ULS) bending stress, biaxial twist, and global buckling.

## 🚀 Key Features

* **Real-Time Parametric Topology:** Dynamically generate Synclastic Domes, Anticlastic Hypars, Kinematic Waves, and Barrel Vaults. Adjust span, height, and UV discretization on the fly.
* **Eurocode 5 (EC5) FEA Diagnostics:** Instant calculation and visual color-mapping of ULS bending stress, structural utilization ratios, and design bending strength ($f_{m,d}$).
* **Constructability & Strain Tracking:** Evaluates geodesic normal divergence to map active physical twisting strain ($\tau_{\text{twist}}$) across timber laths.
* **Dynamic Form-Finding:** Engage dynamic point load simulations and wind velocity forces with real-time deflection tracking against EC5 Serviceability Limit State (SLS) boundaries.
* **High-Performance Rendering:** Utilizes `THREE.InstancedMesh` for rendering thousands of nodal clamps and custom WebGL vertex shaders for fluid, 60FPS load simulations without CPU bottlenecking.
* **Automated BOM Generation:** Export Bill of Materials (BOM) and member-specific structural CSV reports using memory-safe Blob allocation.

## 🛠 Tech Stack

* **Core Graphics:** [Three.js](https://threejs.org/) (r128)
* **Rendering:** WebGL with custom GLSL Vertex Shaders
* **Interface:** Vanilla HTML5, CSS3 (CSS Variables for dynamic theming)
* **Compute:** Vanilla JavaScript (ES6+)

## ⚙️ Installation & Usage

This engine runs entirely client-side. No build steps, bundlers, or servers are required.

1. Clone the repository:
```bash
git clone https://github.com/Samuelson777/timber-gridshell-engine.git

```


2. Open the directory and launch `index.html` in any modern, WebGL-compatible browser (Chrome, Firefox, Edge, Safari).
3. Use the **Scope & Math** panel for engineering context, or hit **H** to toggle the UI for clean viewport rendering.

## 🧮 Engineering Formulation

The engine relies on differential geometry and standardized timber mechanics to approximate stress fields:

* **Design Bending Strength:**

$$f_{m,d} = k_{mod} \cdot \frac{f_{m,k}}{\gamma_M}$$



(Default partial safety factor $\gamma_M = 1.25$, load duration factor $k_{mod} = 0.9$).
* **Curvature Vector:** Evaluates spatial differential curvature to derive active bending moments $M(t) = E \cdot I \cdot \kappa$:

$$\kappa = \frac{\vert{}r'(t) \times r''(t)\vert{}}{\vert{}r'(t)\vert{}^3}$$


* **Global Buckling Criterion:** Computes the critical buckling load index using the continuous shell equivalence parameter:

$$q_{cr} = C \sqrt{E_u \cdot E_v \cdot \left(\frac{t}{R}\right)^2}$$



## 🎯 Conclusion

The Timber Gridshell Computational Engine successfully bridges the gap between conceptual architectural form-finding and rigorous structural engineering. By integrating real-time Eurocode 5 (EC5) compliance checks directly into a WebGL-accelerated environment, the tool collapses the traditional, siloed workflow between architects and engineers.

Its core strength lies in translating complex differential geometry—specifically spatial curvature and biaxial twist—into immediate, actionable feedback regarding ultimate limit state (ULS) bending stress and global buckling. Furthermore, by heavily optimizing the rendering pipeline through GPU-instanced hardware buffers and custom vertex shaders for dynamic load simulation, the engine maintains high-fidelity analytical visualization without sacrificing browser performance. Ultimately, it serves as a robust, enterprise-grade prototype for web-based parametric structural analysis.

## 🔮 Future Enhancements (v9.0+)

To elevate the engine from a high-level diagnostic tool to a comprehensive fabrication-ready platform, the following architectural and computational upgrades are planned:

### 1. Advanced Analytical Engine (FEA & Physics)

* **Non-Linear Finite Element Analysis:** Transition from geometric curvature-based stress approximation to a true non-linear FEA solver capable of calculating large-deflection dynamics and exact shear transfer at the nodes.
* **Anisotropic Material Modeling:** Incorporate timber’s anisotropic properties. Wood behaves differently parallel and perpendicular to the grain; mapping grain direction along the geodesic curves will yield highly accurate localized failure predictions.
* **CFD Wind Integration:** Replace the current sine-wave shader approximation for wind loads with imported Computational Fluid Dynamics (CFD) point-cloud data to simulate realistic, localized wind-pressure coefficients ($C_p$) across complex topographies.

### 2. Fabrication & Interoperability

* **Direct CAM/CNC Export:** Upgrade the BOM export to generate STEP, IGES, or direct G-Code files for 5-axis CNC milling, complete with exact end-cut angles and joint notchings for the laths.
* **Parametric Joint Detailing:** Replace the generic cylindrical node instances with actual parametric joint geometries (e.g., slotted steel plates, shear blocks, or bolting hardware) that dynamically adjust their geometry based on the local intersection angles and calculated shear forces.
* **Custom Topology Import:** Allow users to bypass the mathematical primitives (Dome, Hypar, etc.) by uploading their own base NURBS surfaces or OBJ meshes for the engine to discretize and analyze.

### 3. Optimization & Machine Learning

* **Genetic Algorithm Form-Finding:** Implement an optimization solver that automatically iterates the span, height, and grid divisions to find the configuration that minimizes total timber volume while keeping all EC5 utilization ratios below 90%.
* **Lifecycle Carbon Tracking:** Tie the timber volume and material specs (GL24h, LVL) directly into an environmental product declaration (EPD) database to output a real-time embodied carbon ($CO_2e$) footprint metric alongside the structural diagnostics.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
