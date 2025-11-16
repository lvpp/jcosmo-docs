# Cubic equations of state and mixing rules
In this section, we will examine the development and application of cubic equations of state, beginning with classical models such as the van der Waals equation and progressing to widely adopted forms like the Soave-Redlich-Kwong (SRK) and Peng-Robinson (PR) equations, which are used in JCOSMO. We will also discuss the incorporation of mixing rules, both classical and advanced, which allow these equations to be applied to multicomponent systems.

## Cubic equations of state

To define the thermodynamic state of a pure substance in a single phase, two thermodynamic properties are required. An equation of state provides a mathematical relationship that allows the determination of an unknown property from two known variables. This requires mathematical relations that are functions of temperature (*T*), pressure (*P*), and specific volume (*v*), which are intensive properties that can be determined experimentally [@Koretsky2012].

There are numerous forms of equations of state in the literature, and the most commonly employed are the **cubic equations of state**.  These are third-degree polynomial equations in volume, whose roots can be obtained through various solution methods. A key advantage is that they always yield three roots, allowing for a predictable number of possible solutions [@chao1979equations].

In 1873, van der Waals [@Waals1873] attempted to overcome the limitations of the ideal gas law, which neglects intermolecular forces and assumes that gas molecules occupy negligible volume. He proposed that gas molecules possess finite volume at high pressures and introduced a covolume parameter, *b*, subtracted from the molar volume. To account for molecular interactions, he included the term \(a/v^2\), where *a* represents attractive forces between molecules. The resulting expression is:

$$
P(T, v) = \frac{RT}{v - b} - \frac{a}{v^2}
$$

Here, *a* and *b* are parameters determined from critical point data for pure substances. The parameter *b* represents the molar volume limit as \(P \rightarrow \infty,\) and \(v \rightarrow b \) [@Waals1873].

Based on his work, Redlich and Kwong [@Redlich1949] observed that the \(a/v^2\) term did not account for the influence of temperature on attractive molecular forces. Thus, they introduced a temperature dependency in the attractive term:

$$
P(T, v) = \frac{RT}{v - b} - \frac{a / \sqrt{T}}{v(v + b)}
$$

This modification provided a better representation of several systems. However, as the parameter *a* remained constant, Soave [@Soave1972] proposed a widely used modification, known as SRK (Soave–Redlich–Kwong), where *a* is replaced with a temperature-dependent function \(\alpha\):

$$
\alpha(T_r, \omega) = \left[ 1 + (0.480 + 1.574 \omega - 0.176 \omega^2)(1 - \sqrt{T_r}) \right]^2
$$

Here, \(\omega\) is the acentric factor, and \(T_r = T/T_c\) is the reduced temperature, with \(T_c\) being the critical temperature and *T* the system temperature.

 Peng and Robinson[@Peng1976] evaluated the SRK model for hydrocarbon systems and found it needed improvements, particularly for liquid densities near the critical point. They proposed the following modified expression, altering the volume dependence in the attractive term:

$$
P = \frac{RT}{v - b} - \frac{a \alpha}{v(v + b) + b(v - b)}
$$

The terms *a*, *b*, and \(\alpha(T)\) have the same interpretations as in the SRK model. The \(\alpha(T)\) function was redefined as:

$$
\alpha(T_r, \omega) = \left[ 1 + (0.37464 + 1.54226 \omega - 0.26992 \omega^2)(1 - \sqrt{T_r}) \right]^2
$$

These equations of state are widely implemented in computational tools and offer reasonable estimates for thermodynamic properties. Nevertheless, they do not accurately represent all substances and mixtures. As a result, many modifications have been developed over time to better describe the behavior of diverse systems.

Mathias and Copeman[@Mathias1983] developed an alpha funcition that is a modification designed to enhance the accuracy of PR and SRK equations in predicting fluid phase behavior. The standard alpha functions within these equations can sometimes produce inaccuracies, particularly when dealing with complex mixtures or a wide range of thermodynamic conditions. The Mathias-Copeman alpha function addresses these limitations by introducing additional adjustable parameters (\(c_1\),\(c_2\), and \(c_3\)), thereby providing a more flexible and accurate representation of this temperature dependence. This increased flexibility allows for a better fit to experimental data, improving the equation's ability to model a broader range of substances and conditions. In essence, it acts as a replacement for the original alpha function within these equations, offering a refined approach to modeling the temperature-dependent behavior of fluids. This function is implemented in JCOSMO with the SRK model (SRK-MC).
$$
\alpha_\text{MC}\left(T_r\right)=\left[1+c_1\left(1-\sqrt{T_r}\right)+c_2\left(1-\sqrt{T_r}\right)^2+c_3\left(1-\sqrt{T_r}\right)^3\right]^2
$$

A general form of a cubic equation of state is expressed as:

$$
P(T, v) = \frac{RT}{v - b} - \frac{a(T)}{(v + \epsilon b)(v + \sigma b)}
$$

Where \(\epsilon\) and \(\sigma\) are constants specific to the equation of state used. The parameters *a(T)* and *b* are defined as:

$$
\begin{aligned}
a(T) &= \Psi \frac{\alpha(T_r, \omega) R^2 T_c^2}{P_c} \\
b &= \Omega \frac{RT_c}{P_c}
\end{aligned}
$$

The values of \(\Psi\), \(\Omega\), and \(\alpha(T_r, \omega)\) vary depending on the specific equation of state, as shown below. The subscript *c* refers to the critical point properties. The acentric factor \(\omega\) is defined as [@Pitzer1955]:

$$
\omega = -1 - \log \left[ \frac{P^{\text{sat}}(T_r = 0.7)}{P_c} \right]
$$

Where \(P^{\text{sat}}(T_r = 0.7)\) is the saturation pressure at a reduced temperature of 0.7 \(T_r = 0.7\).

### Table: Parameters of Cubic Equations of State


| Model       | \(\alpha(T_r,\omega)\)                  | \(\epsilon\)     | \(\sigma\)      | \(\Psi\)      | \(\Omega\)     |
|-------------|------------------------------------------|----------------|----------------|-------------|--------------|
| Ideal Gas   | 0                                        | 0              | 0              | 0           | 0            |
| Van der Waals (VDW) | 1                               | 0              | 0              | 27/64       | 1/8          |
| Redlich–Kwong (RK) | \(1/\sqrt{T_r}\)                   | 0              | 1              | 0.42748     | 0.08664      |
| Soave–Redlich–Kwong (SRK) | \(\alpha_\text{SRK}(T_r,\omega)\) | 0      | 1              | 0.42747     | 0.08664      |
| Peng–Robinson (PR) | \(\alpha_\text{PR}(T_r,\omega)\) | \(1 - \sqrt{2}\) | $1 + \sqrt{2}\) | 0.45724     | 0.07780      |

- \(\alpha_\text{SRK}(T_r,\omega) = \left[1 + (0.480 + 1.574 \omega - 0.176 \omega^2)(1 - \sqrt{T_r}) \right]^2\)
- \(\alpha_\text{PR}(T_r,\omega) = \left[1 + (0.37464 + 1.54226 \omega - 0.26992 \omega^2)(1 - \sqrt{T_r}) \right]^2\)
- \(\alpha_\text{MC}\left(T_r\right)=\left[1+c_1\left(1-\sqrt{T_r}\right)+c_2\left(1-\sqrt{T_r}\right)^2+c_3\left(1-\sqrt{T_r}\right)^3\right]^2\)


## Mixing Rules

To enable phase equilibrium calculations and represent mixtures, equations of state require the use of mixing rules. This is necessary because, for cubic equations of state, the parameters \( a \) and \( b \) for mixtures cannot be obtained directly as they are for pure compounds, where critical property data are used. Therefore, mixing rules establish mathematical relationships that relate the mixture parameters \( a \) and \( b \) to the parameters \( a_i \) and \( b_i \) of each pure component \( i \).

### Classic vdW mixing rule

The classic van der Waals mixing rule consists of a linear relation for the covolume \( b \) and a quadratic rule for the attractive parameter \( a \):

$$
\begin{gathered}
a = \sum_{i} \sum_{j} x_{i} x_{j} a_{ij} \\
b = \sum_{i} x_{i} b_{i}
\end{gathered}
$$

where \( a \) is the mixture's attractive parameter, \( b \) is the mixture's covolume, \( x_i \) is the mole fraction of component \( i \), \( b_i \) is the covolume of species \( i \), and \( a_{ij} \) includes both pure component parameters (when \( i = j \)) and interaction parameters (when \( i \neq j \)). The interaction parameters \( a_{ij} \) are calculated using the following combination rule based on a geometric mean:

$$
a_{ij} = \sqrt{a_i a_j}(1 - k_{ij})
$$

Here, \( k_{ij} \) is the binary interaction parameter between components \( i \) and \( j \), typically fitted using experimental phase equilibrium data. While these parameters are often assumed to be zero, they are crucial for mixtures with significant deviations from ideality.
Nevertheless, even with \( k_{ij} \), these classical rule struggle to represent mixtures involving strong molecular interactions, such as polar mixtures (e.g., water and ethanol), due to the absence of temperature-dependent binary parameters [@Smith2007].
By default, all \( k_{ij} = 0 \) within JCOSMO.

### MHV1

Huron and Vidal[@Huron1979] in 1979 proposed a mixing rule based on excess Gibbs energy models \( g^E_\gamma \). They equated the excess Gibbs energy calculated using a cubic equation of state \( g^E_\phi \), at the limit \( P \rightarrow \infty \), to the expression for \( g^E_\gamma \). Under this pressure condition, the molar volume is considered equal to the covolume \( b \), and the expression for the \( a \) parameter is derived.

Following the work of Huron and Vidal[@Huron1979], several other mixing rules were developed, including MHV-1 (Modified Huron-Vidal mixing rule) [@Michelsen1990a] [@Michelsen1990b], UMR (Universal Mixing Rule) [@Voutsas2004], the rule by Wong and Sandler[@Wong1992], and PSRK (Predictive Soave-Redlich-Kwong)[@Holderbaum1991].

Within JCOSMO **MHV-1** can be combined with activity models to include pressure effects in such models.

### PSRK

The PSRK (Predictive Soave-Redlich-Kwong)[@Holderbaum1991] combines the SRK equation with the \( \alpha(T) \) function proposed by Mathias and Copeman shown previously, and a specific UNIFAC parametrization.

To combine the SRK equation of state with the excess Gibbs energy model (UNIFAC), the MHV1 mixing rule was applied:

$$
\begin{gathered}
a = b \left[\frac{g_0^E}{A_1} + \sum_i x_i \frac{a_i}{b_i} + \frac{RT}{A_1} \sum_i x_i \ln \frac{b}{b_i}\right] \\
b = \sum_i x_i b_i
\end{gathered}
$$

where \( g_0^E \) is the excess Gibbs energy in the limit \( P \rightarrow 0 \), calculated using the UNIFAC model. In PSRK, the parameter \( A_1 \) is set to -0.64663. The UNIFAC parameter matrix used in PSRK includes six additional gases, and the most recent revision accepted by the UNIFAC consortium was presented by Horstmann in 2005[@Horstmann2005].

**PSRK** is available within JCOSMO as one of the options for model comparison.

### SCMR

All mixing rules described previously introduce distortions in phase equilibrium calculations at low pressures due to discrepancies between Gibbs excess calculated with the equation of state (\( g^E_\phi \)) and with the activity model (\( g^E_\gamma \)).
Nonetheless, they provide satisfactory results for many mixtures with significant non-ideality, representing an improvement over the classical van der Waals rule.

To overcome this limitation, Staudt and coworkers[@Staudt2012] developed a mixing rule that yields consistent results, where the excess Gibbs energy \( g^E_\phi \) from the equation of state matches the excess Gibbs energy \( g^E_\gamma \) from the activity coefficient model. Due to this consistency, regardless of the cubic equation of state used, the authors named the approach the SCMR (Self-Consistent Mixing Rule). This mixing rule was created by developers of JCOSMO, and it is implemented as an option when calculating phase equilibria. In this mixing rule, the following expression is used to calculate the excess Gibbs energy via an equation of state:

$$
\frac{g^E_\phi}{RT} = \ln \hat{\phi} - \sum_i x_i \ln \phi_i
$$

where \( \hat{\phi} \) is the fugacity coefficient of the mixture, and \( \phi_i \) is the fugacity coefficient of the pure component \( i \), both at the same temperature and pressure.

From this equation, the authors made some assumptions, the main one being that excess volume is negligible. Consequently, they derived the following expression:

$$
q = \frac{1}{I^{Id}} \left( \frac{g^E_\gamma}{RT} - \sum_i x_i \ln \left( \frac{v_i - b_i}{v^{Id} - b} \right) + \sum_i x_i q_i I_i \right)
$$

Here, the superscript \( Id \) denotes the ideal solution reference, the subscript \( i \) refers to each component, \( v \) is the molar volume, and \( q \) and \( I \) are defined as follows:

$$
\begin{aligned}
q_i &\equiv \frac{a_i}{b_i RT} \\
I_i &\equiv I_0 \ln \left( \frac{v_i + \epsilon b_i}{v_i + \sigma b_i} \right) \\
I_0 &= \frac{1}{\sigma - \epsilon}
\end{aligned}
$$

where \( \epsilon \) and \( \sigma \) are constants that depend on the chosen equation of state, as shown in the previous table.

