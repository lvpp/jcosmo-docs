# COSMO-SAC Variants

In this section, we describe the different **COSMO-SAC** variants currently available in **JCOSMO**.

Over the years, several versions of COSMO-SAC have been developed to improve the description of intermolecular interactions, hydrogen bonding, etc. Each variant introduces changes to specific components of the model --- such as the sigma-profile generation, the segment interaction energy expression, or the combinatorial term.

JCOSMO provides the implementation of multiple COSMO-SAC variants, so users can explore their relative performance and applicability.
The variant can be selected via the combobox in the top left corner of JCOSMO user interface, allowing users to benchmark and validate different formulations under consistent computational settings.

> **Note:** Compatibility between sigma profiles and the chosen COSMO-SAC variant is essential. Always ensure that sigma-profiles were generated using the corresponding assumptions (e.g., level of theory, basis set, cavity construction, etc.).

## CS25

The **LVPP-modified COSMO-SAC 2025** model represents our latest COSMO-SAC parametrization, referred to simply as **CS25**.

### Sigma-Profiles

CS25 is based on sigma-profiles calculated using [NWChem](https://nwchemgit.github.io/)[@Apra2020] as the quantum chemical package, in contrast to previous parametrizations that relied on GAMESS.
The level of theory employed is **B3LYP/def2-SVPD**.
Molecular geometries were first optimized in the gas phase, followed by a single-point calculation with the **COSMO** solvation model to generate the sigma-profiles[@Soares2025NWChemCOSMO].

The **def2-SVPD** basis set was chosen as a balance between accuracy and computational cost, offering improved polarization treatment and broader elemental coverage compared to the TZVP basis set used previously.
For larger molecules, the **def2-SVP** basis set was adopted to reduce computational demand, with negligible loss of accuracy in the resulting sigma-profiles.

### Multiple Hydrogen Bond Types

In this parametrization, different types of hydrogen bonds (HBs) are explicitly considered.
Two types of HB donors are defined: one corresponding to water molecules and another representing hydrogens bonded to electronegative atoms such as N, O, F, Cl, Br, or I.
In the user interface, all these donor types are collectively referred to as *alcohol* donors.  

Only the surface area fraction with a charge density exceeding the defined HB cutoff value is assumed to be capable of participating in HBs.

For HB acceptors, several categories are available: *ketone*, *ether*, *amine*, and *F+*.
Some special cases apply to nitrogen-containing groups:

- When nitrogen is bonded to a single atom (e.g., in nitriles), it is treated as a *ketone*-type acceptor.  
- When bonded to two atoms (e.g., in pyridine), it is treated as an *ether*-type acceptor.

### Dispersion Contribution

The original COSMO-SAC model typically disregarded dispersion interactions[@Lin2002], assuming that their effects would cancel out in excess properties.
In **CS25**, a dedicated dispersion contribution is included for each pair of atoms.
This is achieved by storing, along with the surface charge density (sigma-profile), the **atom type** associated with each surface segment.

Although the resulting dispersion term is generally small, it provides a subtle yet meaningful correction that improves the description of nearly athermal mixtures, systems dominated by weak interactions, and particularly **fluorinated/hydrocarbon mixtures**, where dispersion effects play a more significant role.

### Combinatorial contribution

A modified Flory-Huggins (FH) equation is used for the combinatorial contribution[@Kikic1980]:
$$
\ln\ \gamma^{\rm{comb}}_{i} = \ln \frac{\Phi_i'}{x_i} + 1 - \frac{\Phi_i'}{x_i}
$$
where \(\Phi_i' \equiv x_i r_i^p / \sum_j x_j r_j^p\) is the modified volume fraction, \(r_i\) is the molecular volume of compound \(i\) obtained from the COSMO calculations, \(x_i\) is the mole fraction of component \(i\),
and \(p\) is an empirical exponent[@Donohue1975].

This is in contrast to the typical Staverman-Guggenheim (SG) term with a normalized area[@lin2002;@Soares2011].
The reason for using FH is because the potential inconsistencies with the SG formula[@krooshof2024gibbs].

When the exponent \( p = 1 \), the expression reduces to the original FH form.
This classical formula is known to overestimate the combinatorial contribution, effectively providing an upper limit[@Donohue1975].
In **CS25**, an exponent of \( p = \tfrac{2}{3} \) is used, based on comparisons with experimental data for aliphatic hydrocarbons[@Kikic1980].

## COSMO-SAC-HB2

The **LVPP-modified COSMO-SAC** model with multiple hydrogen-bond (HB) energy types, improving the description of systems where different donor and acceptor strengths play a significant role.
Three parametrizations are available, depending on the quantum chemistry package and level of theory used to generate the sigma-profiles:

- **COSMO-SAC-HB2 (GAMESS)** [@Ferrarini2018]: based on sigma-profiles computed with **GAMESS** using the **HF/TZVP** level of theory.  
- **COSMO-SAC-HB2 (FINE)** [@deSouza2025]: based on **TURBOMOLE** calculations employing a fine-grid marching tetrahedron cavity and the **BP/TZVPD** level of theory.  
- **COSMO-SAC-HB2 (BP-TZVP)** [@deSouza2025]: based on **TURBOMOLE** calculations using the **BP/TZVP** level of theory.  

All variants in this section use **FH** as the combinatorial contribution (\(p = 1\) in the modified FH formula), and none includes a dispersive contribution.
