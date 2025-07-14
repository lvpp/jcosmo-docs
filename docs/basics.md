# Modern Quasi-Chemical Theory

In this section, we will explore the foundations of quasi-chemical theory, starting from its original model to the more advanced and modern formulations, such as COSMO-SAC. We will also delve into semi-empirical approximations of the theory, including well-known models like Wilson, NRTL, UNIQUAC, and others. These models have been pivotal in advancing our understanding of solution thermodynamics and play a key role in various applications, including phase equilibria and mixture property prediction.


## Original quasi-chemical model
The **quasi-chemical** model was pioneered by Guggenheim[@guggenheim1952mixtures] in 1940s as a thermodynamic
model to describe the *non-random* arrangement of molecules in a mixture, particularly in liquids.
In its original version, it is based on a lattice picture of the liquid state assuming interactions only between nearest neighbour compounds.

In this framework, interactions can be interpreted as *chemical reactions* at equilibrium. For a binary mixture of compounds *A* and *B*, the following reaction holds:

$$ AA + BB \rightleftharpoons 2 AB $$

When either compound *A* or compound *B* is pure, they can only *interact* with other identical molecules, forming *AA* or *BB* pairs. However, in mixtures, there exists an equilibrium between *AA*, *BB*, and *AB* complexes.

Using the notation introduced by Soares and Staudt[@Soares2023], there should be Boltzmann factor \(\Psi_{AB}\) in terms of the pair formation (or interaction) energy \(u_{AB} = u_{BA}\), given by:

$$
\Psi_{AB} = \exp\left(-\frac{u_{AB}}{kT}\right)    
$$

Then, the probabylity of finding *AB* pairs would be given by:

$$
    \theta_{AB}^2 = \theta_{AA} \theta_{BB} \frac{\Psi_{AB}^2}{\Psi_{AA} \Psi_{BB}}
$$

> **Note:** The above equation is equivalent to the quasi-chemical treatment, Eq.(4.09.1) of Guggenheim[@guggenheim1952mixtures]. If the mixture where to be completely random: \($\theta_{AB} = \Theta_{A} \Theta_{B}\$), where \($\Theta_{A}$\) is the surface area fraction of compound *A* in mixture.

## Extensions in terms of groups or small segments

In its original and simplest form, the quasi-chemical method is expressed in **molecular** terms, which imposes several limitations on the model.
For instance, the model is unable to describe positive excess entropies (found for instance in the acetone/*n*-heptane system).
The simple preference for cross-compound interactions invariably leads to an increase in order within the mixture [@Egner1997].

In a more sophisticated form (assuming the presence of functional groups with different interaction energies), quasi-chemical models become quite flexible.
However, expressing the problem in terms of groups results in an expanded set of equations that need to be solved.
Notably, Panayiotou[@Panayiotou1980] have already presented a formulation in terms of surface area fractions in the 1980s and shortly after Larsen[@Larsen1986] investigated the numerical solution of the resulting system of equations.

The surface fragmentation can be further refined to **small surface segments**, as depicted below[@Soares2023]:

<div style="display: flex; justify-content: space-between;">
  <img src="../img/cosmo-surface.png" alt="First Image" style="width: 45%;"/>
  <img src="../img/cosmo-surface-segments.png" alt="Second Image" style="width: 45%;"/>
</div>

This refinement results in sets of equations equivalent to those used in COSMO-RS [@klamt2005cosmo] or COSMO-SAC [@Lin2002] models. Many studies have recognized COSMO-based models as equivalent to the quasi-chemical treatment [@Klamt2002;@klamt2005cosmo;@Panayiotou2003;@Panayiotou2015;@Soares2023]. 

Elliott [@elliott2023properties] extends this concept by characterizing COSMO-RS/SAC models as Small Segment Quasi-Chemical Theory (SS-QCT), considering them *essentially equivalent*, despite the absence of an explicit lattice reference. 

We prefer to refer to this category of models simply as **modern quasi-chemical** models.

## Semi-empirical approximations

When no additional approximations are assumed, quasi-chemical models lack explicit expressions for activity coefficients, requiring the solution of a set of non-linear equations[@Larsen1986].
Many semi-empirical developments - like Wilson[@Wilson1964], NRTL[@Renon1968], and UNIQUAC[@Abrams1975] - originate from quasi-chemical theory, but their simplifications allow for explicit expressions for the activity coefficients[@Larsen1986].
These models became widely used due to their simplicity and flexibility[@Egner1997].

UNIFAC (UNIQUAC Functional-group Activity Coefficients) original[@Fredenslund1975]
and modified versions like the UNIFAC&nbsp;(Do)[@Lohmann2001]
are still usually very good options when one needs to predict activity coefficients.

