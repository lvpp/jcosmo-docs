# JCOSMO Documentation

Welcome to **JCOSMO documentation!** JCOSMO is a computational tool developed by [LVPP-UFRGS](https://ufrgs.br/lvpp/) for modern quasi-chemical models (*e.g.* COSMO-SAC).

Modern quasi-chemical models are invaluable tools for a wide range of applications in chemistry, materials science, and drug discovery, enabling researchers to make informed decisions and explore novel chemical spaces.

Example of applications:

- Solubilities
- Partition coefficients (e.g. octanol/water)
- Vapor-liquid equilibria
- Liquid-liquid equilibria
- Solid-liquid equilibria
- Screening
- Solvent selection
- Pharmaceuticals
- Extraction processes
- Ionic Liquids
- Deep eutectic solvents
- Electrolyte systems
- Biochemical separations
- Polymer-solvent interactions and equilibria
- Gas absorption
- Lubricant formulation
- etc.

This documentation guides users through installation, usage, theoretical foundations, and advanced features of JCOSMO.

## Getting Started
- [Installation](installation.md)
- [Quick Start Guide](quickstart.md)

## Theory & Models

- [Theory Basics](basics.md)
- [COSMO-SAC variants](cosmo-sac.md)
- [UNIFAC variants](unifac.md)
- [Cubic equations of State and mixing rules](cubic.md)
- [COSMO-SAC-Phi](csp.md)

## Detailed JCOSMO uses

- [Binary mixture charts](binary.md)
- [Profiles, surfaces and pie charts](profiles.md)
- [General mixture calculations](mixture.md)
- [Vapor-Liquid Equilibrium - VLE](vle.md)
- [Liquid-Liquid Equilibrium - LLE](lle.md)
- [Solid-Liquid Equilibrium - SLE](sle.md)

## Advanced Uses

- [Polymer handling](polymer.md)
- [Python interface](python.md)
- [Ionic Liquids](ils.md)
- [Solvent screening](screening.md)

## Contributing

We welcome contributions to improve the **JCOSMO documentation!** If you find errors, have suggestions, or want to contribute new content, please follow these steps to submit a pull request:

1. **Create a GitHub account** (if you don’t have one yet) by signing up [here](https://github.com/join).
2. **Fork the repository**: Navigate to the [JCOSMO Documentation project](https://github.com/lvpp/jcosmo-docs) and click the **Fork** button in the top-right corner.
3. **Clone your fork**: After forking, clone the repository to your local machine using:
    ```bash
    git clone https://github.com/your-username/jcosmo-docs.git
    ```
4. **Make your changes**: Edit the documentation files locally as needed. Be sure to follow the repository's style guide and structure.
5. **Commit your changes**: Once you’re happy with your edits, commit them to your fork using:
    ```bash
    git commit -m "Brief description of changes"
    ```
6. **Push your changes**: Push the committed changes back to your fork on GitHub:
    ```bash
    git push origin main
    ```
7. **Submit a pull request**: Go to the original repository and submit a pull request (PR) with your changes. Make sure to describe the changes you've made and why they are important.

Feel free to also [open an issue](https://github.com/lvpp/jcosmo-docs/issues) if you encounter problems or have questions.
