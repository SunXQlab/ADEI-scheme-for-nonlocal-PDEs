Numerical solver for the nonlinear, phenotypic-structured reaction–diffusion model described in   
Li, F., Li, H., Lin, L., Sun, X.  
 *Mathematical Dissection of Tumor Phenotypic Heterogeneity in a Spatial Data-Informed Nonlocal Reaction–Diffusion Model*  (submitted to *Journal of Mathematical Biology*, 2025)

## 📁 Repository Structure

| File               | Purpose |
|--------------------|---------|
| `ADEI.cpp`         | Single-source C++17 solver to reproduce the Alternating Direction Explicit–Implicit (ADEI) scheme used to generate **Supplementary Figure S1**. |
| `README.md`        | This file. |

## 🛠️ Build & Run (Supplementary Figure S1)

```bash

# 1. Compile (any C++17 compiler)
g++  ADEI.cpp -o ADEI

# 2. Execute 
./ADEI
```

## 🧩 Initial & Boundary Conditions
**· Initial phenotypic distribution**    
C1[i][j][k] = 1e8 * exp(-(x[k]-0.5)^2 / 0.1) (see initial()).  
**· Initial oxygen concentration**     
U1[i][j] = V_u if (i,j) is a vessel point (see is_vessel_point()), otherwise 0.  
**· Neumann (zero-flux) boundaries**   
Implemented via ghost points with mirrored values, e.g., C_{-1,j,k}=C_{1,j,k}.

## 🧮 Domain & Discretisation  
| Quantity        | Variable      | Value      |
| --------------- | ------------- | ---------- |
| Space steps     | `P`           | `100`      |
| Phenotype steps | `Q`           | `50`       |
| Time steps      | `N`           | `3e7`      |
| Spatial Δr      | `p = 0.5 / P` | `0.005 cm` |
| Phenotypic Δx   | `q = 1.0 / Q` | `0.02`     |
| Time step       | `tau`         | `2 s`      |

## 📁 Output Files
| File         | Content                                                                   |
| ------------ | ------------------------------------------------------------------------- |
| `tumor.csv`  | Final cell phenotypic distribution `C[i][j][k]` (`(P+1)×(P+1)×(Q+1)`)     |
| `oxygen.csv` | Final oxygen concentration  `U[i][j]` (`(P+1)×(P+1)`)                     |


## 🎨 Reproduce Other Figures
Edit only the indicated lines in ADEI.cpp:
| Figure    | Variable(s)   | Line numbers (search string)               |
| --------- | ------------- | ------------------------------------------ |
| Fig. 2(a) | `alpha` sweep | `alpha = 1e-14 … 1e-7`                     |
| Fig. 2(b) | `beta` sweep  | `beta  = 1e-14 … 1e-7`                     |
| Fig. 2(c) | `nu` sweep    | `nu    = 1e-5 … 5e-4`                      |
| Fig. 3    | fixed values  | `alpha = 1e-16; beta = 1e-16 etc;`         |
| Fig. 5–6  | initial data  | Replace `initial(x)` & `is_vessel_point()` |
