# Python interface (pyjcosmo)

**pyjcosmo** is the official Python wrapper for JCOSMO.  
It provides a clean and Pythonic interface to the JCOSMO Java gateway, automatically handling data type conversions so users can work with standard Python lists and floats instead of Java arrays.

---

## Overview

`pyjcosmo` enables:

- Direct interaction with JCOSMO from Python
- Automatic Py4J data conversion
- Access to activity coefficients and excess properties
- Database search utilities for compound screening

> **Important:**  
> `pyjcosmo` is a wrapper only.  
> The JCOSMO software must be installed separately and running with the Py4J gateway enabled.

---

## Installation

Install from PyPI:

```bash
pip install pyjcosmo
```

---

## Prerequisites

Before using `pyjcosmo`, ensure:

- JCOSMO is installed
- The JCOSMO Java application is running
- The Py4J Gateway is enabled (default port: `25333`)

If the gateway is not running, the wrapper will not be able to connect.

---

## Quick Start

### 1. List Available Models

```python
import pyjcosmo

jc = pyjcosmo.JCosmoWrapper()
print(jc.list_models())
```

---

### 2. Compute Activity Coefficients and Excess Properties

```python
from pyjcosmo import JCosmoWrapper

jc = JCosmoWrapper()
model = jc.get_model('CS25')

# Set compounds and thermodynamic state
model.set_compounds(['ACETONE', 'CHLOROFORM'])
model.set_temperature(330.15)
model.set_composition([0.5, 0.5])

# Retrieve properties
ln_gamma = model.get_gamma_ln()
he_rt = model.get_excess_enthalpy()
ge_rt = model.get_excess_gibbs()

print(f"lnGamma: {ln_gamma}")
print(f"hE/RT: {he_rt}")
print(f"gE/RT: {ge_rt}")
```

---

### 3. Compound Discovery (Screening)

Search the JCOSMO database by compound name or ion charges.

Example: find all +1 cations.

```python
from pyjcosmo import JCosmoWrapper

jc = JCosmoWrapper()
model = jc.get_model('CS25')

cations = model.find_compounds('+1')

for cat in cations:
    print(f"Found cation: {cat}")
```

This functionality is particularly useful for:

- Ionic liquid screening
- Electrolyte system exploration
- Targeted compound searches
