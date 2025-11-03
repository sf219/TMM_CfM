# Image Coding for Machines via Feature-Preserving Rate-Distortion Optimization (FP-RDO)

Repository for our paper on **FP-RDO**, presented at **TMM**, enabling feature-preserving compression for machine vision tasks.

---

## 📚 Project Documentation

For detailed documentation, tutorials, and project information, visit our [project webpage](https://sf219.github.io/TMM_CfM/).

---

## 🚀 Quick Start with Colab Notebooks

Interact with FP-RDO directly using our Jupyter notebooks in Google Colab:

### 1️⃣ Introduction to FP-RDO
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sf219/TMM_CfM/blob/main/notebooks/01_introduction.ipynb)  

Learn the basics of **Feature-Preserving Rate-Distortion Optimization** and how FP-RDO works.

### 2️⃣ Usage Examples
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sf219/TMM_CfM/blob/main/notebooks/02_usage_examples.ipynb)  

Explore practical applications, including codec integration, machine analysis pipelines, and performance evaluation.

---

## 📖 About FP-RDO

**FP-RDO** is a method for compressing images and videos while preserving features critical for downstream machine vision tasks.  
Key aspects of FP-RDO:

- Optimizes standard codecs (AVC, HEVC) for machine tasks  
- Supports block-wise computation via input-dependent squared error (IDSE)  
- Maintains downstream task accuracy with minimal encoder overhead  
- Standard-compliant

---

## 🗂️ Repository Structure

```text
TMM_CfM/
├── docs/              # Project documentation and website
│   ├── index.md       # Main documentation page
│   └── _config.yml    # GitHub Pages configuration
├── notebooks/         # Interactive Jupyter/Colab notebooks
│   ├── 01_introduction.ipynb
│   ├── 02_usage_examples.ipynb
│   └── README.md
└── README.md          # This file


## 🤝 Contributing

Contributions are welcome! Please feel free to:
- Report bugs and issues
- Suggest new features
- Submit pull requests
- Improve documentation

## 📝 License

See the LICENSE file for details.

## 📧 Contact

For questions or collaboration opportunities, please open an issue on GitHub or reach out to samuelf9@usc.edu.
