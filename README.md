# JCOSMO Documentation  

Welcome to the **JCOSMO Documentation Repository**. This repository contains user guides, tutorials, and reference materials for **JCOSMO**, a tool for COSMO-based modeling and property prediction.  

## About JCOSMO  

**JCOSMO** is a computational chemistry package designed for predicting thermodynamic properties using COSMO-based models and more.

> **Note:** This repository contains documentation only. The JCOSMO software itself is hosted separately and distributed under a different license.  

## License  

The content in this repository is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0) License**.  
You are free to share and adapt the material as long as you provide proper attribution.  

[![CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](https://creativecommons.org/licenses/by/4.0/) 

However, the **JCOSMO software** is distributed under a separate license. For details on its terms and conditions, please refer to the license file included with the JCOSMO installation.

## Contributing  

We welcome contributions to improve the documentation! If you find errors, have suggestions, or want to contribute new content, feel free to open an issue or submit a pull request.  

## Building the Documentation  

This project uses **MkDocs** to generate and serve the documentation. To view it locally, follow these steps:  

### Prerequisites  
Ensure you have **MkDocs** installed. If not, install it using:  

```sh
pip install mkdocs python-markdown-math mkdocs-bibtex mkdocs-material pygments
```  

### Cloning and Serving Locally  
1. **Clone the repository**:  
   ```sh
   git clone https://github.com/your-repo/jcosmo-docs.git
   cd jcosmo-docs
   ```  
2. **Serve the documentation**:  
   ```sh
   mkdocs serve
   ```  
3. **Open the documentation**:  
   - The local development server will start, and you can view the documentation at:  
     **http://127.0.0.1:8000/**  

### Building the Site  
To generate the static site files, run:  
```sh
mkdocs build
```  

### Deploying on GitHub Pages
**For staff only**: After merging a pull request or updating the content, deploy the documentation by running:
```sh
mkdocs gh-deploy
```  

The live documentation is available at [lvpp.github.io/jcosmo-docs/](https://lvpp.github.io/jcosmo-docs/).

For more details, check the [MkDocs documentation](https://www.mkdocs.org/).
