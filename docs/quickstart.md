# Quick Start Guide

Welcome to the **JCOSMO** graphical user interface! This section provides a quick overview to help you get started with JCOSMO and make the most of its powerful modeling capabilities. Check how to **search for compounds**, **view sigma surfaces and profiles**, and **predict activity coefficients, VLE,** and more. Follow the steps in this guide to quickly familiarize yourself with these features and start using JCOSMO effectively for your simulations and analysis.

## Search and select compounds

You can search the database by entering part of a compound's name and hitting ENTER or clicking **`Search`**. Once found, select the desired compound and use the  **`Add`** button or hit ENTER again.
The selected compounds are used it in the calculations available in **JCOSMO**.

<div style="position: relative; display: inline-block; width: 100%;">
  <img src="../img/jcosmo-search.png" alt="JCOSMO Initial Screen" style="width: 100%; height: auto;" />
  
  <!-- Highlighted Region: Using percentage-based positioning -->
  <div style="position: absolute; top: 17%; left: 28%; width: 32%; height: 6%; border: 3px solid rgba(255, 255, 0, 0.8); background-color: rgba(255, 255, 0, 0.3);"></div>
</div>

## View sigma-surfaces

Once you have selected one or more molecules, you can view the sigma-surfaces by clicking the **`View Surfaces`** button:

<div style="position: relative; display: inline-block; width: 100%;">
  <img src="../img/jcosmo-surfaces.png" alt="JCOSMO Initial Screen" style="width: 100%; height: auto;" />
  
  <!-- Highlighted Region: Using percentage-based positioning -->
  <div style="position: absolute; top: 86%; left: 50%; width: 10%; height: 6%; border: 3px solid rgba(255, 255, 0, 0.8); background-color: rgba(255, 255, 0, 0.3);"></div>
</div>

For each compound, the COSMO 3D surface of induced charge densities (sigma-surface) is shown.  
The standard color convention is: **green** for neutral (apolar) regions, **red** for induced positive charges, and **blue** for induced negative charges.  

These induced charges arise due to differences in electronegativity between atoms within a molecule. For example, oxygen is highly electronegative and tends to attract electron density, inducing a **positive charge** (shown in red). Conversely, hydrogen atoms in polar bonds (such as O-H or N-H) tend to lose electron density and thus induce a **negative charge** (shown in blue) on themselves.  

This charge distribution is obtained using the **COSMO method**, which models the molecule as being embedded in a **perfect conductor**, similar to a liquid metal. This approximation allows the calculation of charge polarization at the molecular surface, leading to the sigma-surface representation.  

In addition to the sigma-surface, the compound's molecular volume, surface area, and molar mass are also displayed.


## Activity coefficients, Excess, and Mixture properties

If exactly two compounds are selected, the **`Binary`** tab can be used to display the activity coefficient chart.
Just click on  **`Calculate`** and the logarithm of the activity coefficients chart is calculated.

Recalling that when a compound is pure, \(\ln \gamma_i = 0\), and when its mole fraction tends to zero, we reach the infinite dilution limit: \(\ln \gamma_i = \ln \gamma_i^\infty\).
The actual infinite dilution values are also displayed at the bottom of the page:

<div style="position: relative; display: inline-block; width: 100%;">
  <img src="../img/jcosmo-lngamma.png" alt="JCOSMO Initial Screen" style="width: 100%; height: auto;" />
  
  <div style="position: absolute; top: 22%; left: 85%; width: 10%; height: 6%; border: 3px solid rgba(255, 255, 0, 0.8); background-color: rgba(255, 255, 0, 0.3);"></div>

  <div style="position: absolute; top: 86%; left: 65%; width: 28%; height: 5%; border: 3px solid rgba(255, 255, 0, 0.8); background-color: rgba(255, 255, 0, 0.3);"></div>
</div>

When mixing **cyclohexane** and **sec-butanol**, the mixture shows **positive deviations from ideality**, meaning the **logarithm of the activity coefficients are positive** with the compounds **thermodynamically uncomfortable** in the mixture compared to their pure states. In this case, this behavior arises mainly from differences in **molecular interactions**. Sec-butanol molecules can form **hydrogen bonds** with each other. Introducing cyclohexane disrupts these interactions, reducing the stabilization provided by hydrogen bonding.

The user can also play with the checkboxes at the top:

 - `ln Gamma`: displays the logarithm of the activity coefficients (default)
 - `Excess`: displays the mixture excess properties
 - `Mixture`: displays the mixture properties, recalling excess Gibbs and Entropy differ from mixture Gibbs and Entropy
 - `Dimensionless (1/RT)`: dimensionless (or divided by RT) properties are used (default), otherwise `J/mol` or `J/g` are used
 - `Mass based`: Use mass-based calculations instead of the default molar basis


## Sigma profiles

A **sigma profile** is a molecule-specific distribution of charge density across a solute's surface, used in COSMO-based models to describe intermolecular interactions. It represents the fraction of the surface area associated with a given screening charge density (\( \sigma \)).  

Now, let's view a **sigma profile** in JCOSMO. Simply navigate to the **`Profile`** tab and click **`Refresh`**—the profiles for all selected compounds will be displayed.

<div style="position: relative; display: inline-block; width: 100%;">
  <img src="../img/jcosmo-profiles.png" alt="JCOSMO Initial Screen" style="width: 100%; height: auto;" />
  
  <div style="position: absolute; top: 13%; left: 64%; width: 7%; height: 6%; border: 3px solid rgba(255, 255, 0, 0.8); background-color: rgba(255, 255, 0, 0.3);"></div>

  <div style="position: absolute; top: 18%; left: 92%; width: 6%; height: 6%; border: 3px solid rgba(255, 255, 0, 0.8); background-color: rgba(255, 255, 0, 0.3);"></div>
</div>

Cyclohexane is a nonpolar molecule, meaning its **sigma profile** is concentrated around **zero charge density**. This indicates a surface largely free of significant electrostatic interactions, making cyclohexane a typical example of a **neutral, nonpolar solvent** in COSMO-based models.

For **sec-butanol**, the presence of the **hydroxyl (-OH) group** introduces regions of **polarization**. The **oxygen atom** in the hydroxyl group tends to **accumulate electron density**, leading to **induced positive charge densities** on nearby surface segments. Conversely, the **hydrogen** of the hydroxyl group becomes **electron-deficient**, contributing to **negative induced charge densities**. However, despite these polar contributions, a **substantial portion** of sec-butanol’s surface remains **neutral**, reflecting the balance between its **hydrophobic alkyl chain** and **hydrophilic hydroxyl group**.

This difference in sigma profiles explains why cyclohexane cannot donate or accept hydrogen bonds, while sec-butanol can participate in hydrogen bonding while still retaining some nonpolar character.

## VLE — vapor-liquid equilibrium

To predict an **isothermal vapor-liquid equilibrium (VLE)**, navigate to the **`VLE`** tab and click **`Recalc`**. This will generate the equilibrium data based on the selected model.  

Please note that **two compounds** must be selected before proceeding with the prediction. You can also compare the predictions with other models (e.g. **UNIFAC (Do)**) by selecting it in the **comparison combobox**, as shown below:

<div style="position: relative; display: inline-block; width: 100%;">
  <img src="../img/jcosmo-vle.png" alt="JCOSMO Initial Screen" style="width: 100%; height: auto;" />
  
  <div style="position: absolute; top: 13%; left: 72%; width: 7%; height: 6%; border: 3px solid rgba(255, 255, 0, 0.8); background-color: rgba(255, 255, 0, 0.3);"></div>

  <div style="position: absolute; top: 23%; left: 83%; width: 12%; height: 6%; border: 3px solid rgba(255, 255, 0, 0.8); background-color: rgba(255, 255, 0, 0.3);"></div>
</div>

By default, the predictions are based on the assumption that **modified Raoult's law** holds:
$$ P y_i = x_i \gamma_i P_i^{sat}$$

In this system, the VLE exhibits **positive deviations** from ideal behavior, the **activity coefficients** are greater than one, reflecting the **unfavorable interactions** between the components. These interactions cause the components to escape into the vapor phase more readily, increasing the **bubble pressure** compared to an ideal mixture.

### Comparison with experimental data

In addition to pure predictions, **JCOSMO** can also compare model responses with experimental data. To do this, simply select **`Experiment...`** and navigate to a text file containing the experimental data.

<div style="position: relative; display: inline-block; width: 100%;">
  <img src="../img/jcosmo-vle-exp.png" alt="JCOSMO Initial Screen" style="width: 100%; height: auto;" />
  
  <div style="position: absolute; top: 18%; left: 61%; width: 12%; height: 6%; border: 3px solid rgba(255, 255, 0, 0.8); background-color: rgba(255, 255, 0, 0.3);"></div>
</div>

JCOSMO includes a small selection of experimental data in its **data** folder:

```
jcosmo3
├── jcosmo.exe
├── jcosmo.sh
├── data
│ ├── vle # Vapor-Liquid Equilibrium
│ ├── lle # Liquid-Liquid Equilibrium
│ ├── sle # Solid-Liquid Equilibrium
│ ├── ...
└── ...
```

For the cyclohexane/sec-butanol system, experimental data is available for **323.15 K**. When this experimental file is selected, the results shown above are displayed.

For this particular case, both the selected **COSMO-SAC** variant and **UNIFAC (Do)** produce predictions that closely match the available experimental data, including the azeotrope. However, **COSMO-based models**, such as **COSMO-SAC**, offer several advantages over group contribution methods like **UNIFAC**.  

One key advantage is that COSMO-based models rely on information derived from quantum chemistry calculations. Unlike **UNIFAC**, which uses predefined group interactions that have to be calibrated with experimental data.
Thus, COSMO-based models are **less reliant on empirical data** and can be applied to a broader range of systems, including those with limited or no group contributions. This makes COSMO-based models particularly useful for systems with complex interactions or for predicting properties of new, uncharacterized compounds.


## LLE — liquid-liquid equilibrium

JCOSMO also provides a framework for predicting **liquid-liquid equilibrium (LLE)**, navigate to the **`LLE`** tab and click **`Recalc`**.

> Please note that **two compounds** must be selected before proceeding with the prediction.
Additionally, LLE occurs when a binary or multicomponent liquid mixture separates into two immiscible liquid phases at equilibrium. This phase separation is mostly driven by differences in molecular interactions.

However, not all binary mixtures will undergo phase separation. Some systems remain fully miscible across all compositions. In that case, no predictions will be made.

If the Gibbs energy curve exhibits a double-well shape with a common tangent, the mixture is predicted to split into two liquid phases.

In JCOSMO, the compositions of the two coexisting phases (\( x^{\alpha} \) and \( x^{\beta} \)) at the initial temperature point are determined using a dividing rectangles global search algorithm. If a valid two-phase system is identified for the selected mixture, subsequent calculations follow the isoactivity criterion for liquid phases \( \alpha \) and \( \beta \):

$$ x_i^{\alpha} \gamma_i^{\alpha} = x_i^{\beta} \gamma_i^{\beta} $$

As for VLEs, the user can perform either pure predictions by clicking on **`Recalc`** or compare the results with experimental data by selecting the **`Experiment...`** button.
Results for the system *n*-pentanol/water are shown below:

<div style="position: relative; display: inline-block; width: 100%;">
  <img src="../img/jcosmo-lle-exp.png" alt="JCOSMO Initial Screen" style="width: 100%; height: auto;" />
</div>



## SLE — solid-liquid equilibrium

JCOSMO can also perform **solid-liquid equilibrium (SLE)** calculations.
The standard calculations assume a pure compound in the solid phase, surrounded by a liquid phase. Under this assumption, and with the further considerations that there is no phase transition and that the heat capacity difference between the solid and liquid phases is negligible, the following relation holds:

$$ x_i \gamma_i = \exp \left( \frac{ -\Delta H_i^{\text{fus}} \left( 1 - \frac{T}{T_i^{\text{fus}}} \right)}{ R T } \right) $$

where:

- \( x_i \) is the mole fraction of the solute in the liquid phase,
- \( \gamma_i \) is the activity coefficient of the solute in the liquid phase,
- \( \Delta H_i^{\text{fus}} \) is the solute enthalpy of fusion,
- \( T_i^{\text{fus}} \) is the solute fusion temperature,
- \( R \) is the universal gas constant,
- \( T \) is the absolute temperature.

> Note that JCOSMO can also predict SLE with up to two solid transition temperatures and with a non-zero heat capacity difference between solid and liquid.

As usual, the user can perform either pure predictions by clicking on **`Recalc`** or compare the results with experimental data by selecting the **`Experiment...`** button.
Results for the system glucose/water system are shown below:

<div style="position: relative; display: inline-block; width: 100%;">
  <img src="../img/jcosmo-sle-exp.png" alt="JCOSMO Initial Screen" style="width: 100%; height: auto;" />
</div>