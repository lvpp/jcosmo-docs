# Ionic Liquids

JCOSMO provides native support for **ionic liquids (ILs)**.  
An ionic liquid is treated as a combination of a **cation** and an **anion**, and can be handled either:

- As separate ions (explicit multicomponent mixture), or  
- As a single **pseudo-compound** written in bracket notation.

---

## Nomenclature

In JCOSMO, ionic liquids follow the standard bracket notation:

```
[ CATION ][ ANION ]
```

Example:

```
[BMIM][BF4]
```

Internally, JCOSMO searches the database using the charged species:

- `BMIM+1`
- `BF4-1`

If both species exist, the ionic liquid pseudo-compound is created and added to the selected compounds list.

---

## Adding an Ionic Liquid via the Graphical Interface

In the JCOSMO user interface:

1. Click **"Add Salt..."**
2. A dialog appears listing available cations and anions
3. Select the desired pair
4. Click **Accept**

The ionic liquid will be added automatically to the selected compounds list.

Internally, JCOSMO retrieves the corresponding charged species from the database and builds the pseudo-compound representation.

---

## Direct Name Entry

Users may also type the full pseudo-compound name directly:

```
[BMIM][BF4]
```

If the corresponding ions exist in the database, JCOSMO will recognize and construct the ionic liquid automatically.

---

## Working with Ions vs. Pseudo-Compound

JCOSMO allows two modeling approaches:

### 1. Explicit Ion Representation

You may add:

- `BMIM+1`
- `BF4-1`

The system becomes a **multicomponent mixture**, where each ion is treated as an independent species.

This approach is useful for:
- Electrolyte systems
- Ion-specific analysis
- Mixtures with additional salts

---

### 2. Ionic Liquid as a Pseudo-Compound

You may instead use:

```
[BMIM][BF4]
```

In this case:

- The IL behaves as a single neutral compound
- The mixture remains simpler (fewer components)
- Suitable for typical IL–solvent systems

This is generally the preferred approach when treating the ionic liquid as a molecular entity.

---

## Multivalent Ions

If the valence is not +1 and −1, the stoichiometry is reflected explicitly in the name.

Example:

If the anion has charge −2:

- `CO3-2`

and the cation has charge +1:

- `DEA+1`

The ionic liquid name becomes:

```
[DEA]2[CO3]
```

This indicates that two cations are required to balance one divalent anion.

JCOSMO automatically enforces charge neutrality when constructing the pseudo-compound.

---

## Database Behavior

When adding an ionic liquid:

- JCOSMO searches the database for the charged species
- Validates charge balance
- Builds the pseudo-compound representation
- Adds it to the selected compounds list

If one of the ions is missing from the database, the ionic liquid cannot be constructed.

---

## Recommendations

- Use the **"Add Salt..."** dialog whenever possible to avoid naming mistakes.
- Use the pseudo-compound notation for standard IL-solvent systems.
- Use explicit ions for electrolyte or ion-specific studies.
- Ensure that the database contains the required charged species before defining a new IL.
