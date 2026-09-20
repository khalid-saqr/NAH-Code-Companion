# Nonlinear Arterial Hemodynamics — Code Companion

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_01_VascuQuest_Companion.ipynb)
[![VascuQuest](https://img.shields.io/badge/VascuQuest-public%20repository-181717?logo=github)](https://github.com/KNOWDYN/VascuQuest)
[![PWDB](https://img.shields.io/badge/PWDB-Zenodo%203275625-1682D4)](https://zenodo.org/records/3275625)

This repository contains the **eight executable Google Colab companions** to *Nonlinear Arterial Hemodynamics*. There is one notebook for each of Chapters 1–8.

The notebooks reproduce selected mechanics from the book, test limiting cases and numerical consistency, expose parameter dependence, place selected models in virtual-population context through [VascuQuest](https://github.com/KNOWDYN/VascuQuest), and generate reproducible figures and data products.

> **The book is self-contained.** The notebooks are optional computational companions. No definition, derivation, physical argument, or conclusion in the book requires the reader to execute code.

The relationship is deliberately asymmetric:

- **the book defines** the mechanics, nomenclature, assumptions, reductions, and scientific claims;
- **the notebooks reproduce, test, visualize, and extend** those mechanics computationally;
- **VascuQuest supplies reproducible source-data access and population context**, not replacement physics.

---

## Table of contents

- [Quick start](#quick-start)
- [The eight notebooks](#the-eight-notebooks)
- [Notation used in this README](#notation-used-in-this-readme)
- [VascuQuest and PWDB](#vascuquest-and-pwdb)
- [How to read the notebooks](#how-to-read-the-notebooks)
- [Chapter-by-chapter guide](#chapter-by-chapter-guide)
  - [Chapter 1: The Classical Picture of Arterial Hemodynamics](#chapter-1-the-classical-picture-of-arterial-hemodynamics)
  - [Chapter 2: The Mechanical Limits of Wall Shear Stress](#chapter-2-the-mechanical-limits-of-wall-shear-stress)
  - [Chapter 3: Womersley Flow as the Classical Reference State](#chapter-3-womersley-flow-as-the-classical-reference-state)
  - [Chapter 4: Constitutive Anisotropy and Transverse Dynamics](#chapter-4-constitutive-anisotropy-and-transverse-dynamics)
  - [Chapter 5: Geometry-Parameterized Spectral Dynamics](#chapter-5-geometry-parameterized-spectral-dynamics)
  - [Chapter 6: Wall Compliance and Mean Transport](#chapter-6-wall-compliance-and-mean-transport)
  - [Chapter 7: Nonlinear Arterial Hemodynamics](#chapter-7-nonlinear-arterial-hemodynamics)
  - [Chapter 8: Computing the Theory](#chapter-8-computing-the-theory)
- [Reproducibility outputs](#reproducibility-outputs)
- [Deterministic representative-subject rule](#deterministic-representative-subject-rule)
- [Interpretation boundaries](#interpretation-boundaries)
- [Reproducibility and evidence discipline](#reproducibility-and-evidence-discipline)
- [Repository layout](#repository-layout)
- [Data and software provenance](#data-and-software-provenance)
- [Recommended reading workflow](#recommended-reading-workflow)
- [Scope](#scope)

## Quick start

The released execution contract is **Google Colab + Run all**.

1. Open the notebook for the chapter you are reading.
2. In Colab, choose **Runtime → Run all**.
3. Allow the notebook to install its pinned VascuQuest revision and acquire only the PWDB artifacts it needs.
4. Let the notebook execute sequentially. There are no widgets, hidden branches, or manual subject choices in the released workflows.
5. Inspect the generated <code>figures/</code>, <code>data/</code>, and reproducibility manifest under the notebook-specific <code>/content/nonlinear_arterial_hemodynamics_chXX/</code> directory.

The notebooks pin VascuQuest to commit [<code>8307147d72e7a6f3ea3135895bd6f52927c67439</code>](https://github.com/KNOWDYN/VascuQuest/commit/8307147d72e7a6f3ea3135895bd6f52927c67439) and use the canonical Pulse Wave DataBase (PWDB) Zenodo record [<code>3275625</code>](https://zenodo.org/records/3275625), DOI [<code>10.5281/zenodo.3275625</code>](https://doi.org/10.5281/zenodo.3275625).

> **Local Jupyter execution is not the reference workflow.** The notebooks use Colab paths rooted at <code>/content/</code>. Local execution is possible after adapting those paths, but the reproducibility contract tested for this companion is a clean Colab runtime followed by **Run all**.

---

## The eight notebooks

| Ch. | Book chapter | Notebook | Primary computational responsibility |
|---:|---|---|---|
| 1 | **The Classical Picture of Arterial Hemodynamics** | [GitHub](Notebooks/Chapter_01_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_01_VascuQuest_Companion.ipynb) | Poiseuille and pulsatile reference mechanics, dimensionless balances, harmonic representation, and virtual-population context for the classical scales. |
| 2 | **The Mechanical Limits of Wall Shear Stress** | [GitHub](Notebooks/Chapter_02_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_02_VascuQuest_Companion.ipynb) | Boundary-versus-volume information, constructive same-WSS counterexamples, velocity–vorticity structure, near-wall integration, and information compression. |
| 3 | **Womersley Flow as the Classical Reference State** | [GitHub](Notebooks/Chapter_03_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_03_VascuQuest_Companion.ipynb) | Exact harmonic transfer functions, flow-rate and wall-shear response, asymptotic limits, and multiharmonic rigid-Womersley reconstruction. |
| 4 | **Constitutive Anisotropy and Transverse Dynamics** | [GitHub](Notebooks/Chapter_04_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_04_VascuQuest_Companion.ipynb) | Coupled axial–azimuthal dynamics, isotropic recovery, vorticity channels, Lamb-vector observables, and controlled constitutive sensitivity. |
| 5 | **Geometry-Parameterized Spectral Dynamics** | [GitHub](Notebooks/Chapter_05_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_05_VascuQuest_Companion.ipynb) | Fourier pseudospectral evolution, spectral redistribution, energy diagnostics, mechanism-off tests, and separation of resolved geometry from reduced coefficient parameterization. |
| 6 | **Wall Compliance and Mean Transport** | [GitHub](Notebooks/Chapter_06_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_06_VascuQuest_Companion.ipynb) | Finite-wavenumber compliant response, second-order streaming, moving-interface traction, limiting-case recovery, and wall-motion/pressure–area context. |
| 7 | **Nonlinear Arterial Hemodynamics** | [GitHub](Notebooks/Chapter_07_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_07_VascuQuest_Companion.ipynb) | Common quadratic convolution examined through separate constitutive, geometry, and compliance branches without constructing an additive multiphysics model. |
| 8 | **Computing the Theory** | [GitHub](Notebooks/Chapter_08_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_08_VascuQuest_Companion.ipynb) | Numerical representation, transforms, Bessel evaluation, radial solvers, pseudospectral evolution, finite differences, quadrature, convergence, and provenance. |

A convenience bundle of the eight notebooks is also available at [<code>Notebooks/Notebooks.zip</code>](Notebooks/Notebooks.zip).


---

## Notation used in this README

The notation below follows the book. Every mathematical symbol used later in this README is defined here before its first scientific use.

| Symbol | Definition |
|---|---|
| $r$ | radial coordinate. |
| $R$ | vessel radius. |
| $x=r/R$ | normalized radial coordinate. |
| $z$ | dimensional axial coordinate. |
| $t$ | dimensional time. |
| $p$ | pressure. |
| $\partial$ | partial-derivative operator. |
| $\nabla$ | spatial gradient operator; $\nabla^2$ is the Laplacian. |
| $G=-\partial p/\partial z$ | axial pressure-gradient forcing; positive $G$ drives positive axial flow. |
| $\rho$ | fluid density. |
| $\mu$ | dynamic viscosity. |
| $\nu=\mu/\rho$ | kinematic viscosity. |
| $Q$ | volumetric flow rate. |
| $U$ | source flow-velocity waveform used by the VascuQuest flow reconstruction. |
| $A$ | luminal cross-sectional area; when aligned source quantities are available, VascuQuest reconstructs $Q=UA$. |
| $\Omega$ | fundamental angular frequency. |
| $m$ | temporal harmonic index. |
| $\Omega_m=m\Omega$ | angular frequency of temporal harmonic $m$. |
| $\alpha=R\sqrt{\Omega/\nu}$ | fundamental Womersley number. |
| $\alpha_m=\sqrt{m}\,\alpha$ | Womersley number of temporal harmonic $m$. |
| $\delta_W$ | fundamental viscous penetration depth, with $\delta_W/R=\sqrt{2}/\alpha$. |
| $\tau_w$ | wall shear stress. |
| $\widehat{\tau}_w$ | complex harmonic wall-shear amplitude. |
| $\mathbf n$ | unit normal to the wall. |
| $\boldsymbol\sigma$ | Cauchy stress tensor. |
| $\mathbf I$ | identity tensor. |
| $\boldsymbol\tau_w$ | exact tangential wall-traction vector, $\boldsymbol\tau_w=(\mathbf I-\mathbf n\mathbf n)\boldsymbol\sigma\mathbf n$. |
| $\mathbf u$ | fluid velocity vector. |
| $u_z$ | axial velocity component. |
| $u_\theta$ | azimuthal velocity component. |
| $\mathbf e_z$ | axial unit basis vector. |
| $\mathbf e_\theta$ | azimuthal unit basis vector. |
| $\omega_\theta$ | azimuthal vorticity component. |
| $\omega_z$ | axial vorticity component. |
| $\boldsymbol\ell$ | Lamb vector. |
| $\ell_r$ | radial component of the Lamb vector. |
| $\Delta\ell_r$ | anisotropic increment in radial Lamb-vector response; superscripts $\mathrm{aniso}$ and $\mathrm{iso}$ label anisotropic and isotropic states. |
| $\mathcal A_{ij}$ | constitutive-coefficient tensor entries used in Chapter 4; $i$ and $j$ are constitutive-direction indices. |
| $L_0$ | axial reference length used in the Chapter 5 reduction. |
| $\zeta=z/L_0$ | reduced axial coordinate. |
| $T_0$ | reference time used in the Chapter 5 reduction. |
| $s=t/T_0$ | reduced time. |
| $\widetilde a$ | reduced axial disturbance field in Chapter 5. |
| $\kappa$ | spatial reduced wavenumber conjugate to $\zeta$ in Chapter 5. |
| $k$ | dimensional traveling-wave wavenumber used in the compliant-wave formulation. |
| $b(\zeta)$ | reduced dispersive coefficient in the conceptual Chapter 5 model. |
| $g(\zeta)$ | reduced dissipative coefficient in the conceptual Chapter 5 model. |
| $c_0$ | exponent parameter entering the Chapter 5 fractional damping operator. |
| $I_2$ | total quadratic spectral-energy diagnostic used in Chapter 5. |
| $\mathcal R_{\mathrm{spec}}$ | spectral-broadening diagnostic; it is not total-energy growth and is unrelated to vessel radius $R$. |
| $\mathcal M_G$ | explicit geometry-to-reduced-coefficient map; the subscript $G$ denotes geometry in this map, not the pressure-gradient variable $G$. |
| $R_c$ | centerline curvature radius, distinct from vessel radius $R$. |
| $\epsilon$ | small wall-motion parameter used for the Chapter 6 perturbation expansion. |
| $O(\epsilon^n)$ | asymptotic order in that expansion; $n$ is the perturbation-order index. |
| $\mathbf u_1$ | first-order oscillatory velocity field. |
| $\mathbf u_2$ | second-order velocity field. |
| $u_{1z}$ | axial component of $\mathbf u_1$. |
| $u_{2z}$ | axial component of $\mathbf u_2$. |
| $p_2$ | second-order pressure. |
| $\eta_1$ | first-order wall displacement. |
| $\langle\cdot\rangle$ | average over one forcing period. |
| $\langle Q_{\mathrm{stream}}\rangle$ | period-averaged second-order streaming flow rate. |
| $\langle\tau_w^{(2)}\rangle$ | period-averaged second-order fluid-on-wall traction in the Chapter 6 convention. |
| $K_s$ | wall stiffness parameter in the Chapter 6 wall model; the subscript $s$ is a stiffness label, not the reduced-time variable $s$. |
| $\tau_v$ | wall viscoelastic time parameter; the subscript $v$ labels the viscoelastic contribution. |
| $T_w$ | wall-tension parameter; the subscript $w$ labels the wall. |
| $\rho_w h_w$ | wall areal inertia; $\rho_w$ is wall density and $h_w$ is wall thickness. |
| $j\in\{C,G,B\}$ | Chapter 7 branch label: constitutive ($C$), geometry-parameterized ($G$), or compliant-boundary ($B$); here branch label $G$ is distinct from the pressure-gradient variable $G$. |
| $\mathbf q_j$ | state vector for branch $j$. |
| $\mathcal L_{0,j}$ | reference linear operator for branch $j$. |
| $\Delta\mathcal L_j$ | branch-specific change to the reference linear operator. |
| $\mathcal N_j$ | branch-specific quadratic nonlinear operator. |
| $\mathbf f_j$ | forcing for branch $j$. |
| $\Gamma_E$ | logarithmic reduced-wave energy growth/decay diagnostic used in Chapter 8 verification of Case B; the subscript $E$ denotes energy. |

Unless a chapter explicitly nondimensionalizes a calculation, the notebooks use the common blood properties $\rho=1060\ \mathrm{kg\,m^{-3}}$, $\mu=3.5\times10^{-3}\ \mathrm{Pa\,s}$, and $\nu=\mu/\rho$.

Two spectral indices must remain distinct: $m$ is a **temporal harmonic index**, whereas $\kappa$ is a **spatial reduced wavenumber**. They belong to different transforms and must not be identified.

## VascuQuest and PWDB

[VascuQuest](https://github.com/KNOWDYN/VascuQuest) is the data/provenance layer used by these companions. It provides reproducible access to supported PWDB quantities and geometry while preserving evidence provenance.

The notebooks distinguish among:

- **source quantities** read from supported PWDB artifacts;
- **reconstructed quantities**, such as volumetric flow obtained from aligned velocity and area as $Q=UA$;
- **derived quantities** computed from the equations of the book;
- **modelled quantities** produced by an explicit reduced model or branch-specific projection.

This distinction matters. A PWDB observation is not automatically a theorem of the book, and a reduced-model projection is not a source measurement.

PWDB <code>VirtualSubject</code> entries are virtual haemodynamic simulation instances, not patients. Population and age-group plots in these notebooks are therefore **virtual-population context**, not in-vivo epidemiological laws.

The notebook-facing physiological inputs include combinations of radius, heart rate, pressure, flow velocity, luminal area and source-supported geometry, depending on chapter. VascuQuest does **not** provide a native wall-shear-stress field for these notebooks; when a notebook constructs a reference WSS projection, it is identified as a model-derived quantity rather than PWDB-native WSS.

---

## How to read the notebooks

Each notebook follows the same scientific spine:

1. **Chapter question** — the physical question owned by that chapter.
2. **Book mechanics used here** — equations and assumptions reproduced from the text.
3. **VascuQuest representation** — how source data are mapped into book variables.
4. **Deterministic reconstruction** — reference mechanics and benchmark quantities.
5. **VascuQuest exploration** — parameter or population context where scientifically meaningful.
6. **Mechanism-focused results** — the quantities that answer the chapter question.
7. **What the reader should learn** — the intended physical interpretation.
8. **Chapter-enrichment candidates** — figures/results that may be useful beyond the notebook.
9. **Reproducibility record** — generated artifacts, provenance, and execution state.

Not every exploratory notebook figure belongs in the printed book. The book promotes only figures that add nonredundant physical understanding; convergence plots, source-mapping diagnostics, sensitivity sweeps, and population context may remain notebook-only.

---

## Chapter-by-chapter guide


## Chapter 1: The Classical Picture of Arterial Hemodynamics

**Question:** What does the classical Poiseuille–Womersley–WSS description resolve, and where does that information reside?

[Open notebook on GitHub](Notebooks/Chapter_01_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_01_VascuQuest_Companion.ipynb)

The notebook reconstructs the steady and pulsatile reference mechanics and then uses VascuQuest to place the classical scales in virtual-population context.

Key ideas to follow:

- Poiseuille flow is a **field solution**, not merely a resistance formula.
- Wall shear stress is an exact boundary traction within the reference model, but it is still a boundary quantity derived from the resolved field.
- Reynolds number and Womersley number organize different balances.
- A periodic waveform contains multiple temporal harmonics, and harmonic $m$ experiences $\alpha_m=\sqrt m\,\alpha$.
- The chapter's clarity comes from deliberate exclusions: no anisotropy, geometry-sensitive modulation, wall compliance, or nonlinear synthesis is introduced here.

Useful outputs include the normalized Poiseuille field, Womersley-number population context, harmonic-content diagnostics, source metadata, deterministic representative-subject metadata, and a reproducibility manifest.

---

## Chapter 2: The Mechanical Limits of Wall Shear Stress

**Question:** What mechanically relevant information is lost when a wall traction is used as a surrogate for the neighboring fluid volume?

[Open notebook on GitHub](Notebooks/Chapter_02_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_02_VascuQuest_Companion.ipynb)

The exact tangential traction is

```math
\boldsymbol\tau_w
=
(\mathbf I-\mathbf n\mathbf n)\,\boldsymbol\sigma\mathbf n.
```

The notebook then constructs distinct interior velocity fields with the same wall gradient and therefore the same Newtonian WSS, while their volumetric quantities differ.

Key ideas to follow:

- WSS is **not mechanically deficient at the wall**; the limitation is representational when it is asked to stand in for a volume state.
- Same-WSS counterexamples can have different $Q$, vorticity, and Lamb-vector fields.
- In fully developed classical flow, a finite Lamb vector can coexist with zero convective acceleration because the kinetic-energy gradient cancels it through the Gromeka–Lamb identity.
- The endothelial pillbox is a near-wall **volume integration**, not a redefinition of surface traction.
- Nonlinear products must be formed after real-field reconstruction, or by the mathematically equivalent convolution.

The VascuQuest part is descriptive. Its scalar reference-state WSS projection is **not actual pulsatile PWDB WSS** and is not used as proof of the chapter mechanics.

---

## Chapter 3: Womersley Flow as the Classical Reference State

**Question:** What does the rigid, straight, isotropic Womersley solution predict under harmonic forcing, and what does it exclude?

[Open notebook on GitHub](Notebooks/Chapter_03_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_03_VascuQuest_Companion.ipynb)

This notebook is the frequency-response reference for the later chapters.

Key ideas to follow:

- Harmonic pressure forcing produces radius-dependent velocity amplitude and phase.
- Flow rate and WSS have different transfer functions and therefore different amplitude/phase responses as $\alpha$ changes.
- The low-$\alpha$ limit must recover the Poiseuille solution.
- The high-$\alpha$ limit separates an inertia-dominated core from a near-wall viscous layer with $\delta_W/R=\sqrt2/\alpha$.
- Multiharmonic superposition remains linear at the velocity-equation level, but different harmonics experience different $\alpha_m$ and therefore different radial/temporal filtering.

PWDB supplies physiological inputs such as $R$, $\Omega$, and $Q(t)$; the notebook maps those inputs into the **rigid-Womersley reference model**. Those outputs are model projections, not claims that PWDB itself is a rigid-wall Womersley simulation.

---

## Chapter 4: Constitutive Anisotropy and Transverse Dynamics

**Question:** Can constitutive directionality alone open transverse dynamics in the straight rigid-tube Womersley problem?

[Open notebook on GitHub](Notebooks/Chapter_04_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_04_VascuQuest_Companion.ipynb)

The kinematic state is extended to

```math
\mathbf u(r,t)
=
u_\theta(r,t)\mathbf e_\theta
+
u_z(r,t)\mathbf e_z,
```

where $u_\theta$ and $u_z$ are the azimuthal and axial components of $\mathbf u$, respectively. The transverse degree of freedom is opened **constitutively**, not geometrically.

Key ideas to follow:

- the coupled radial operators follow from the stated cylindrical constitutive law and are not interchangeable;
- switching off the off-diagonal constitutive ratios must recover scalar Womersley flow and force $u_\theta\to0$ and $\omega_z\to0$;
- classical Womersley flow already contains $\omega_\theta$; the constitutive extension opens the additional axial-vorticity channel $\omega_z$;
- the inertial comparison is the anisotropic increment, with $\mathrm{aniso}$ denoting the anisotropic state and $\mathrm{iso}$ the isotropic reference,

```math
\Delta\ell_r
=
\ell_r^{(\mathrm{aniso})}
-
\ell_r^{(\mathrm{iso})};
```

- nonlinear force spectra are constructed only after reconstructing the real velocity/vorticity fields.

VascuQuest supplies classical physiological context such as radius, heart rate and waveform forcing. It does **not** supply or calibrate the anisotropy tensor $\mathcal A_{ij}$.


---

## Chapter 5: Geometry-Parameterized Spectral Dynamics

**Question:** Can geometry-parameterized axial dynamics redistribute perturbation energy toward shorter axial scales while total quadratic energy still decays?

[Open notebook on GitHub](Notebooks/Chapter_05_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_05_VascuQuest_Companion.ipynb)

The conceptual reduced equation is

```math
\frac{\partial \widetilde a}{\partial s}
+\widetilde a\frac{\partial\widetilde a}{\partial\zeta}
+b(\zeta)\frac{\partial^3\widetilde a}{\partial\zeta^3}
+g(\zeta)\left(-\partial_\zeta^2\right)^{(1+c_0)/2}\widetilde a
=0.
```

For the canonical calculations, $c_0=0$, so the dissipative Fourier symbol is proportional to $|\kappa|$.

Key ideas to follow:

- nonlinear steepening couples spatial Fourier modes;
- dispersion changes phase without being the source of total quadratic-energy decay in the constant-coefficient periodic case;
- damping removes quadratic energy and acts more strongly on shorter axial scales;
- $\mathcal R_{\mathrm{spec}}$ measures spectral broadening/redistribution, not energy growth;
- the conceptual variable-coefficient model and the numerically advanced spatially averaged model are distinct levels of reduction.

The canonical Case B calculation provides a useful numerical anchor:

```math
I_2(0)=6.911504,
\qquad
I_2(10)\approx4.984669,
\qquad
\mathcal R_{\mathrm{spec}}(10)\approx10.11474.
```

PWDB geometry is used to document arterial geometric scales and context. The notebook does **not** silently convert source geometry into $b$ or $g$: the geometry-to-coefficient map $\mathcal M_G$ requires an explicit modeling decision or calibration.

---

## Chapter 6: Wall Compliance and Mean Transport

**Question:** Can a compliant wall convert a zero-mean oscillatory mode into persistent time-averaged transport through nonlinear self-interaction?

[Open notebook on GitHub](Notebooks/Chapter_06_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_06_VascuQuest_Companion.ipynb)

The perturbation order is explicit; $O(\epsilon^n)$ denotes terms of order $n$ in the small wall-motion parameter $\epsilon$:

```math
O(\epsilon):\ \text{oscillatory mode},
```

```math
O(\epsilon^2):\ \text{mean field and second harmonic},
```

```math
O(\epsilon^3):\ \text{envelope solvability}.
```

At second order, the period-averaged momentum equation contains the Reynolds-stress forcing

```math
\mu\nabla^2\langle\mathbf u_2\rangle
-\nabla\langle p_2\rangle
=
\rho\left\langle
(\mathbf u_1\cdot\nabla)\mathbf u_1
\right\rangle.
```

The moving-wall boundary condition contributes at the same order:

```math
\left\langle u_{2z}(R)\right\rangle
=
-\left\langle
\eta_1
\left.\frac{\partial u_{1z}}{\partial r}\right|_R
\right\rangle.
```

Key ideas to follow:

- compliance changes the boundary condition rather than merely modifying a coefficient in the rigid solution;
- finite-$k$ motion introduces radial velocity and radial pressure structure;
- steady streaming is the zero-frequency response of a quadratic interaction;
- the bulk Reynolds-stress forcing and the quadratic moving-wall boundary term are distinct $O(\epsilon^2)$ sources;
- mean flux and moving-interface mean traction are distinct observables and require different evaluation rules.

For the canonical normalized Case C verification setting, the book/notebook reference values include

```math
\langle Q_{\mathrm{stream}}\rangle
\approx
7.5686\times10^{-9}\ \mathrm{m^3\,s^{-1}},
```

and the complete fluid-on-wall second-order traction is approximately

```math
\langle\tau_w^{(2)}\rangle
\approx
-2.1862\times10^{-4}\ \mathrm{Pa}.
```

These are **verification values**, not a calibrated arterial wall. VascuQuest provides wall-motion and pressure–area waveform context; it does not uniquely identify $K_s$, $\tau_v$, $T_w$, or $\rho_w h_w$ without a separate inverse model.

---

## Chapter 7: Nonlinear Arterial Hemodynamics

**Question:** What mechanical structure is genuinely common to the constitutive, geometry-parameterized, and compliant branches?

[Open notebook on GitHub](Notebooks/Chapter_07_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_07_VascuQuest_Companion.ipynb)

Chapter 7 is a **synthesis chapter**, not a fourth governing-model branch. Its branch-indexed form is

```math
\mathcal L_{0,j}\mathbf q_j
+
\Delta\mathcal L_j\mathbf q_j
+
\mathcal N_j(\mathbf q_j,\mathbf q_j)
=
\mathbf f_j,
\qquad
j\in\{C,G,B\}.
```

The common algebra is pairwise quadratic interaction. In harmonic form, output index $m$ is assembled from input pairs whose indices sum to $m$; the zero-frequency mean is therefore the $m=0$ member of the same convolution structure rather than a separate nonlinear algebra.

Key ideas to follow:

- the constitutive branch modifies the admissible local velocity/vorticity state before the nonlinear product is formed;
- the geometry branch exposes spatial mode coupling and redistribution;
- the compliant branch projects oscillatory self-interaction onto zero frequency and mean transport;
- local force density, temporal spectrum, spatial redistribution, and mean flux are **different observables with different dimensions and state spaces**.

There is **no Case D**, no additive anisotropy–geometry–compliance PDE, and no scalar “arterial nonlinearity score” in this repository.

---

## Chapter 8: Computing the Theory

**Question:** What numerical machinery is required to reproduce and test the theory without obscuring the mechanics?

[Open notebook on GitHub](Notebooks/Chapter_08_VascuQuest_Companion.ipynb) · [Open in Colab](https://colab.research.google.com/github/khalid-saqr/NAH-Code-Companion/blob/main/Notebooks/Chapter_08_VascuQuest_Companion.ipynb)

Every numerical workflow begins with a representation contract:

1. What field is being represented?
2. In which coordinate is that field smooth or periodic?
3. Which exact or limiting solution must be recovered?

The notebook implements the three canonical verification paths:

- **Case A — constitutive coupling:** radial BVP, regularity, tolerance refinement, and isotropic recovery;
- **Case B — spectral redistribution:** split Fourier pseudospectral evolution, $2/3$ de-aliasing, refinement, and the quadratic-energy identity;
- **Case C — compliant streaming:** analytical finite-$k$ first-order mode, second-order radial mean solve, moving-wall closure, flux, traction, and cross-discretization verification.

The numerical lessons are as important as the final numbers:

- transform normalization is part of the implementation contract;
- analytical differentiation is a valuable numerical reference when available;
- convergence alone is not enough if the wrong boundary-value problem is being solved;
- mechanism-off tests are physical verification tests;
- quadrature measure is part of the observable definition;
- parameter provenance must remain explicit.

For Case C, the companion retains both the canonical benchmark path and an independent fourth-order radial path. The final book uses them as a **cross-discretization convergence check**: agreement of the refined physical observable is the verification target; identical coarse-grid trajectories are not required.

The VascuQuest section is deliberately separate from Cases A–C. It demonstrates deterministic source-to-book mapping and provenance; it does not replace canonical numerical verification.

![VascuQuest source-to-book reproducibility map](Notebooks/ch08_vascuquest_reproducibility_map.png)


---

## Reproducibility outputs

A successful notebook run writes a chapter-specific set of reproducibility artifacts. Depending on the chapter, these include:

- publication-quality black-and-white PDF figures and high-resolution PNG previews;
- numerical benchmark tables and convergence data;
- VascuQuest/PWDB verification metadata;
- deterministic representative-subject records where a representative subject is used;
- population or representative-case data behind the plotted results;
- a final reproducibility manifest.

The notebooks are designed so that figures remain interpretable in black-and-white. Physical distinctions use line style, marker, grayscale, hatching, or direct labeling rather than color alone.

---

## Deterministic representative-subject rule

When a notebook needs a single virtual subject for an illustrative reconstruction, it does not hand-pick one. The notebooks use the same deterministic rule:

1. use the middle PWDB source age stratum;
2. select the median canonical subject identifier within that stratum.

The corresponding subject metadata are written to the reproducibility outputs.

---

## Interpretation boundaries

These notebooks intentionally refuse several tempting shortcuts:

- **Chapter 2:** a Poiseuille-equivalent scalar WSS projection is not presented as actual pulsatile PWDB WSS.
- **Chapter 3:** PWDB waveforms are projected into the rigid Womersley reference model; that projection is not a statement that PWDB obeys the rigid model.
- **Chapter 4:** VascuQuest does not provide or calibrate the anisotropy tensor.
- **Chapter 5:** source geometry is not silently converted into reduced coefficients $b$ and $g$.
- **Chapter 6:** pressure–area loops do not uniquely identify the Kelvin–Voigt wall parameters without an explicit inverse problem.
- **Chapter 7:** branch-specific observables are not collapsed into an additive multiphysics state or scalar nonlinearity score.
- **Chapter 8:** VascuQuest provenance is not a substitute for mathematical/numerical verification.

These boundaries are part of the scientific content, not merely software cautions.

---

## Reproducibility and evidence discipline

A numerical result should be interpreted only after its status is clear:

- **exact relation** — follows analytically from the stated model;
- **reduced model** — follows from an explicit reduction or closure;
- **numerical computation** — generated by a stated discretization and verified by refinement or limiting-case recovery;
- **VascuQuest/PWDB observation** — descriptive result from the virtual source population;
- **model projection using PWDB inputs** — book model evaluated with source-derived inputs;
- **hypothesis or interpretation** — not to be confused with any of the above.

The notebooks are structured to keep these categories visible throughout the computation.

---

## Repository layout

~~~text
NAH-Code-Companion/
├── README.md
└── Notebooks/
    ├── Chapter_01_VascuQuest_Companion.ipynb
    ├── Chapter_02_VascuQuest_Companion.ipynb
    ├── Chapter_03_VascuQuest_Companion.ipynb
    ├── Chapter_04_VascuQuest_Companion.ipynb
    ├── Chapter_05_VascuQuest_Companion.ipynb
    ├── Chapter_06_VascuQuest_Companion.ipynb
    ├── Chapter_07_VascuQuest_Companion.ipynb
    ├── Chapter_08_VascuQuest_Companion.ipynb
    ├── Notebooks.zip
    └── ch08_vascuquest_reproducibility_map.png
~~~

---

## Data and software provenance

### VascuQuest

Public repository: [KNOWDYN/VascuQuest](https://github.com/KNOWDYN/VascuQuest)

Pinned notebook revision:

~~~text
8307147d72e7a6f3ea3135895bd6f52927c67439
~~~

VascuQuest is the supported interface used here for dataset identity, acquisition, quantity/site semantics, provenance, and reproducible source-to-book mapping.

### Pulse Wave DataBase (PWDB)

Canonical Zenodo record: [3275625](https://zenodo.org/records/3275625)  
DOI: [10.5281/zenodo.3275625](https://doi.org/10.5281/zenodo.3275625)

Research using PWDB source data should cite the PWDB scholarly source independently of any citation for the VascuQuest software layer.

---

## Recommended reading workflow

For the closest correspondence between theory and computation:

1. read the chapter's **Overview** and governing derivation in the book;
2. open the matching notebook and read its **Chapter question** before running code;
3. execute **Run all** from a clean Colab runtime;
4. compare the notebook's mechanism-off or limiting-case result with the chapter reference state;
5. inspect the **What the reader should learn** section before interpreting population plots or reduced-model projections;
6. use Chapter 8 when you need the numerical representation, convergence logic, quadrature rules, or verification hierarchy behind Chapters 4–6.

This ordering keeps the computation subordinate to the physical argument rather than allowing implementation detail to define the science.

---

## Scope

This repository is the code companion to Chapters 1–8. It is **not**:

- a replacement for the book;
- a clinical decision tool;
- an in-vivo patient database;
- a universal arterial solver;
- a calibrated multiphysics arterial model combining all mechanisms at once;
- evidence that virtual-population associations are causal physiological laws.

Its purpose is narrower and more useful: to make the book's mechanics **inspectable, reproducible, testable, and computationally explorable** without changing the scientific architecture of the text.
