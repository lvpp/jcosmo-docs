**This page is currently under development and will be available soon. Stay tuned for updates!**

# UNIFAC
Introduced as a group-contribution method for the prediction of activity coefficients in nonelectrolyte liquid mixtures, UNIFAC model (UNIQUAC Functional-group Activity Coefficients) was proposed in 1975 by Fredenslund et al.

In group-contribution methods a molecule is built by several functional groups, and a physical property is the sum of the contributions made by the functional groups that compose the molecule. For mixtures this approach is attractive because it allows for the reuse of functional groups for different molecules, allowing a better representation of the chemical space with a lower expenditure. 

The molecular activity coefficient is made of two parts, one combinatorial and one residual:

$$  
  \ln \gamma_{i} = \underbrace{\ln \gamma_{i}^{C}}_\text{combinatorial} + \underbrace{\ln \gamma_{i}^{R}_\text{residual}}
$$

\begin{itemize}
    \item Combinatorial: provides the contribution due to differences in molecular size and shape.
    \item Residual: provides the contribution due to molecular interactions.
\end{itemize}

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
\begin{equation}
    \Psi_{mn} = exp - \left[\frac{U_{mn}-U_{nm}}{RT}\right] = exp - (a_{mn}/T)
\end{equation}

UNIFAC pioneered the use of group-contribution on models for the prediction of activity coefficients of non-electrolytes, and showed good success on predicting binary and multi-component mixtures where little or no experimental data was available.

Inside JCOSMO several UNIFAC variants are available, they will described briefly in the following sections.

## UNIFAC-LLE
As a development to the original UNIFAC model, in 1981 Magnussen et al. proposed a parameter table specially calculated for Liquid-Liquid Equilibira (LLE). Changing the data used for estimation of the UNIFAC prameters from VLE data to LLE data reduced the AAD for ternary LLE systems in almost 80\%.

While UNIFAC-LLE is limited to the available parameters, it still has some advantages when working with molecules and systems that were part of the parameter estimation process.

## UNIFAC(Do)
With the purpose of calculating vapor-liquid equilibria, activity coefficients at infinite dilution and enthalpies of mixing with just one set of parameters, Gmehling modified the UNIFAC method with what is now known as UNIFAC(Do) - (Modified UNIFAC - Dortmund).

## UNIFAC-NIST
As more experimental data becomes available, there is a need for periodic updates of the parameter matrix of models to reflect the most recent information for phase equilibrium. UNIFAC-NIST is a modified UNIFAC (with the same expression that of UNIFAC(Do) for both the combinatorial and residual contributions) with model parameters estimated with critically evaluated phase equilibrium data including vapor–liquid equilibrium (VLE), liquid–liquid equilibrium (LLE), solid–liquid equilibrium (SLE), excess enthalpy (HE), infinite dilution activity coefficient (IDAC) and excess heat capacity (CPE) data. Data collected within the NIST SOURCE Data Archival System and processed through NIST ThermoData Engine were used in the parameter optimization process. 
