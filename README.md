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

## Building the Documentation and Contributing

This project uses **MkDocs** to generate and serve the documentation. To view it locally or to make corrections or additions, follow these steps:  

### Prerequisites  

Ensure you have **Python 3** support and **MkDocs** installed.

If you don't have Python installed, please follow these steps:

1. **Download Python**: Visit the [official Python website](https://www.python.org/downloads/) and download the latest version suitable for your operating system.
2. **Install Python**: Follow the installation instructions. Make sure to check the option to add Python to your system’s PATH during the installation process.
3. **Verify Installation**: After installation, verify Python is installed correctly by running the following command in your terminal or command prompt:

```sh
python --version
```

Make sure you have Python version 3 or newer.

If you don't have **MkDocs** and the other dependencies installed, install it using:

```sh
pip install mkdocs python-markdown-math mkdocs-bibtex mkdocs-material pygments
```  

### Work on your own fork and test it locally

1. **Create a GitHub account** (if you don’t have one yet) by signing up [here](https://github.com/join).
2. **Fork the repository**: Navigate to the [JCOSMO Documentation project](https://github.com/lvpp/jcosmo-docs) and click the **Fork** button in the top-right corner.
3. **Clone your fork**: After forking, clone the repository to your local machine using:
    ```bash
    git clone https://github.com/your-username/jcosmo-docs.git
    ```
4. **Make your changes**: Edit the documentation files locally as needed. Be sure to follow the repository's style guide and structure.
5. **Serve the documentation**:  
   ```sh
   mkdocs serve
   ```  
6. **Open the documentation**:  
   - The local development server will start, and you can view the documentation at:  
     **http://127.0.0.1:8000/**  
7. **Commit your changes**: Once you’re happy with your edits, commit them to your fork using:
    ```bash
    git commit -m "Brief description of changes"
    ```
8. **Push your changes**: Push the committed changes back to your fork on GitHub:
    ```bash
    git push origin main
    ```
9. **Submit a pull request**: Go to your forked repository and submit a pull request (PR) with your changes. Make sure to describe the changes you've made and why they are important.


### Deploying on GitHub Pages
**For staff only**: After merging a pull request or updating the content, deploy the documentation by running:
```sh
mkdocs gh-deploy
```  

The live documentation is available at [lvpp.github.io/jcosmo-docs/](https://lvpp.github.io/jcosmo-docs/).

For more details, check the [MkDocs documentation](https://www.mkdocs.org/).
