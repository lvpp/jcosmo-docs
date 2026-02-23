# Ionic Liquids

JCOSMO provides native support for **ionic liquids (ILs)**.

In normal use, ionic liquids should be defined as a **single pseudo-compound (ion pair)** using bracket notation, for example:

```
[BMIM][BF4]
```

This is the **recommended and default approach**.

Working with individual ions is possible, but is intended only for advanced electrolyte modeling.

---

## Recommended Approach: Ion Pair (Pseudo-Compound)

In JCOSMO, ionic liquids are normally handled as neutral ion pairs using the bracket notation:

```
[ CATION ][ ANION ]
```

Example:

```
[BMIM][BF4]
```

Internally, JCOSMO:

- Searches the database for `BMIM+1`
- Searches the database for `BF4-1`
- Validates charge balance
- Automatically constructs the neutral pseudo-compound

The resulting ionic liquid behaves as a **single compound** in the mixture.

This approach:

- Ensures automatic electroneutrality
- Prevents charge imbalance errors
- Keeps the mixture definition simple
- Is appropriate for most IL–solvent systems

---

## Adding an Ionic Liquid (Graphical Interface)

To add an ionic liquid:

1. Click **"Add Salt..."**
2. Select the desired cation
3. Select the desired anion
4. Click **Accept**

JCOSMO automatically creates the pseudo-compound and adds it to the selected compounds list.

This method avoids naming errors and is strongly recommended.

---

## Direct Name Entry

Instead of using **Add Salt...**, you may type the full ion pair directly:

```
[BMIM][BF4]
```

If both ions exist in the database, JCOSMO will construct the pseudo-compound automatically.

---

## Multivalent Ions

If charges are not +1 and −1, stoichiometry is reflected explicitly in the name.

Example:

- `DEA+1`
- `CO3-2`

The ionic liquid becomes:

```
[DEA]2[CO3]
```

JCOSMO automatically enforces charge neutrality when constructing pseudo-compounds.

---

## Advanced Use Only: Explicit Ion Representation

It is possible to add the ions separately:

- `BMIM+1`
- `BF4-1`

In this case, the system becomes a **multicomponent ionic mixture**.

> ⚠️ **Important — Manual Electroneutrality Required**
>
> When working with explicit ions, the user must manually ensure that the total mixture charge is zero:
>
> ```
> Σ (zi · xi) = 0
> ```
>
> where:
>
> - `zi` is the ionic charge  
> - `xi` is the mole fraction  
>
> JCOSMO does **not** automatically enforce electroneutrality in explicit-ion mode.
>
> This makes the explicit-ion approach significantly more error-prone.

For standard ionic liquid–solvent systems, the pseudo-compound notation (e.g., `[BMIM][BF4]`) should always be preferred.

---

## Abbreviated Names for Ions

JCOSMO uses standardized abbreviated names for ionic liquid species.

Common cations:

- `EMIM` — 1-ethyl-3-methylimidazolium  
- `BMIM` — 1-butyl-3-methylimidazolium  
- `HMIM` — 1-hexyl-3-methylimidazolium  

Common anions:

- `BF4` — tetrafluoroborate  
- `PF6` — hexafluorophosphate  
- `BTI` — bis(trifluoromethylsulfonyl)imide  
- `DCA` — dicyanamide  

The internal database stores the charged forms (e.g., `BMIM+1`, `BF4-1`), but users should normally work with the neutral ion pair notation.

---

## Database Behavior

When an ionic liquid is defined as a pseudo-compound:

- JCOSMO searches for the charged species
- Verifies charge balance
- Constructs the neutral ion pair
- Adds it to the mixture as a single compound

If one of the required ions is missing from the database, the ionic liquid cannot be constructed.

---

## Recommendation

For nearly all ionic liquid applications:

- Use the **ion pair pseudo-compound notation**
- Prefer the **"Add Salt..."** dialog
- Avoid explicit-ion mode unless performing electrolyte-specific modeling

The pseudo-compound approach is safer, simpler, and less prone to modeling errors.
