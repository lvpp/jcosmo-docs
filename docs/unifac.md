**This page is currently under development. Stay tuned for updates!**

# UNIFAC
Introduced in 1975 by Fredenslund et al. [@Fredenslund1975], the UNIFAC model (UNIQUAC Functional-group Activity Coefficients) is a group-contribution method developed for predicting activity coefficients in nonelectrolyte liquid mixtures. In this approach, molecules are represented as assemblies of functional groups, with thermodynamic properties estimated as the sum of contributions from these individual groups. This method is particularly advantageous for mixture modeling, as it enables the reuse of group parameters across different compounds, expanding coverage of the chemical space while reducing the need for extensive experimental data.



In UNIFAC, the molecular activity coefficient is made of two parts, one combinatorial and one residual:

$$  
  \ln \gamma_{i} = \ln \gamma_{i}^{C} + \ln \gamma_{i}^{R}
$$


- **Combinatorial**: provides the contribution due to differences in molecular size and shape.
- **Residual**: provides the contribution due to molecular interactions.

The combinatorial part is taken as the same as the one in UNIQUAC – designed in a group-contribution scope – without modification.

$$
    \ln \gamma_{i}^{C} = \ln\frac{\Phi_{i}}{x_{i}} + \frac{z}{2}q_{i}\ln\frac{\theta_{i}}{\Phi_{i}} + l_{i} - \frac{\Phi_{i}}{x_{i}} \sum_{j}x_{j}l_{j}
$$

$$
    l_{J} = \frac{z}{2} \left(r_{i} - q_{i} \right) - \left( r_{i} -1 \right)_{i}
$$

$$
    z = 10
$$

$$
    \theta_{i} = \frac{q_{i}x_{i}}{\sum_{j}q_{j}x_{j}}
$$

$$
    \Phi_{i} = \frac{r_{i}x_{i}}{\sum_{j}r_{j}x_{j}}
$$

$$
    r_{i} = \sum_{k} \nu_{k}^{(i)} R_{k}
$$

$$
     {q_{i} = \sum_{k}\nu_{k}^{(i)} Q_{k} {a}}
$$

Residual contribution is calculated by the solution-of-groups concept, and is defined as:

$$
    \ln \gamma_{i}^{R} = \underbrace{\sum_{k}\nu_{k}^{(i)}[\ln \Gamma_{k} - \ln \Gamma_{k}^{(i)}]}_\text{all groups}
$$

The group activity coefficient $\Gamma_{k}$ is found from a similar equation to UNIQUAC's residual contribution:

$$
   \ln \Gamma_{k} = Q_{k} \left [1 - \ln(\sum_{m}\Theta_{m}\Psi_{mk}) - \sum_{m}\left(\frac{\Theta_{m} \Psi_{km}}{\sum_{n}\Theta_{n} \Psi_{nm}}\right)\right]
$$

$\Theta_{m}$ is calculated in a similar way to $\theta_{i}$:

$$
    \Theta_{m} = \frac{Q_{m}X_{m}}{\sum_{n}Q_{n}X_{n}}
$$

The groups interaction parameter $\Psi_{mn}$ is given by:

$$
    \Psi_{mn} = exp - \left[\frac{U_{mn}-U_{nm}}{RT}\right] = exp - (a_{mn}/T)
$$

UNIFAC pioneered the use of group-contribution on models for the prediction of activity coefficients of non-electrolytes, and showed good success on predicting binary and multi-component mixtures where little or no experimental data was available. It's initial scope of compounds and temperature range was expanded with new developments. Inside JCOSMO several UNIFAC variants are available, in the following sections these variants will be described briefly.

## UNIFAC-LLE
As a development to the original UNIFAC model, in 1981 Magnussen et al.[@Magnussen1981] proposed a parameter table specially calculated for Liquid-Liquid Equilibira (LLE). Changing the data used for estimation of the UNIFAC prameters from VLE data to LLE data reduced the AAD for ternary LLE systems in almost 80\%.

While UNIFAC-LLE is limited to the available parameters, it still retain some advantages when working with molecules and systems that were part of the parameter estimation process.

## UNIFAC(Do)
With the purpose of calculating vapor-liquid equilibria, activity coefficients at infinite dilution and enthalpies of mixing with just one set of parameters, Weidlich and Gmehling [@Weidlich1987] modified the UNIFAC method with what is now known as UNIFAC(Do) - (Modified UNIFAC - Dortmund).

## UNIFAC(PSRK)
The application of cubic equations of state (EoS) for the description of systems with supercritical compounds is a way to reduce the deviations in the model’s predictions. For this purpose an approach with a coupled  Soave-Redlich-Kwong (SRK) equation with the original UNIFAC model was developed, UNIFAC(PSRK) [@Holderbaum1991]. This model allows an accurate prediction of phase equilibrium in a wide temperature and pressure range. Beside phase equilibria, equations of state provide other thermodynamic properties (enthalpies, densities). 

## UNIFAC-NIST
As more experimental data becomes available, there is a need for periodic updates of the parameter matrix of models to reflect the most recent information for phase equilibrium. UNIFAC-NIST[@Kang2011] is a modified UNIFAC (with the same expression that of UNIFAC(Do) for both the combinatorial and residual contributions) with model parameters estimated with critically evaluated phase equilibrium data including vapor–liquid equilibrium (VLE), liquid–liquid equilibrium (LLE), solid–liquid equilibrium (SLE), excess enthalpy (HE), infinite dilution activity coefficient (IDAC) and excess heat capacity (CPE) data. Data collected within the NIST SOURCE Data Archival System and processed through NIST ThermoData Engine were used in the parameter optimization process. 
