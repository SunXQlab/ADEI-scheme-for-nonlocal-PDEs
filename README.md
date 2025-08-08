Numerical solver for the nonlinear, phenotypic-structured reaction–diffusion model described in
Li, F., Li, H., Lin, L., Sun, X.  
 *Mathematical Dissection of Tumor Phenotypic Heterogeneity in a Spatial Data-Informed Nonlocal Reaction–Diffusion Model*  
(submitted to *Journal of Mathematical Biology*, 2025)

## 📁 Repository Structure

| File               | Purpose |
|--------------------|---------|
| `ADEI.cpp`         | Single-source C++17 solver to reproduce the Alternating Direction Explicit–Implicit (ADEI) scheme used to generate **Supplementary Figure S1**. |
| `README.md`        | This file. |

## 🛠️ Build & Run (Supplementary Figure S1)

```bash
# 1. Clone
git clone https://github.com/your-github-username/tumor-heterogeneity-adei.git
cd tumor-heterogeneity-adei

# 2. Compile (any C++17 compiler)
g++ -std=c++17 -O3 ADEI.cpp -o ADEI

# 3. Execute (parameter sweep over α)
./ADEI
