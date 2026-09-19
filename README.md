# Knowledge Graphs from the NIH ChestX-ray14 Dataset

A knowledge graph construction pipeline built on the NIH ChestX-ray14 dataset. It combines tabular metadata and image-derived features to represent relationships between patients, findings, and diagnostic labels.

## 🎯 Project Overview

Chest X-ray datasets contain information in two forms: structured tabular metadata (patient demographics, disease labels, view position) and the raw images themselves.

This project builds a **dual-pipeline** approach to compare how knowledge graphs built from each source differ, and to explore combining them into a richer multimodal representation.

## 🧪 Methodology

Two parallel pipelines are implemented and compared:

1. **CSV / Tabular pipeline**: builds graph entities and relations directly from the structured metadata (patient ID, findings, follow-up visits, demographics).
2. **Direct multimodal pipeline**: extracts image-level features using pretrained CNN and transformer backbones (**ResNet**, **DenseNet**, **ViT**, **CLIP**) and adds them as graph node features alongside the tabular data.

A **patient-disjoint split** is used throughout. No patient's images appear in both the training and evaluation subsets, which avoids data leakage caused by patient-level correlation.

## 📊 Key Components

- Pretrained feature extraction with ResNet, DenseNet, ViT, and CLIP backbones
- Patient-disjoint dataset construction to prevent leakage
- Knowledge graph assembly linking patients, findings, and extracted features
- Comparison of tabular-only and multimodal graph representations

## 📁 Repository Structure

```
.
├── image Vs CSV.ipynb   # Dual-pipeline notebook: tabular vs. image-based KG construction
├── LICENSE              # MIT License
└── README.md
```

## 🗂️ Dataset

This project uses the **NIH ChestX-ray14** dataset, released by the NIH Clinical Center. It contains over 100,000 frontal-view chest X-ray images with labels for 14 common thoracic diseases, plus patient metadata.

- Download: [NIH Clinical Center release](https://nihcc.app.box.com/v/ChestXray-NIHCC) (also mirrored on Kaggle)
- The images and raw data are **not included** in this repository because of their size. Download them from the source above and update the file paths in the notebook to match your setup.

**Citation:**

> Wang, X., Peng, Y., Lu, L., Lu, Z., Bagheri, M., & Summers, R. M. (2017). *ChestX-ray8: Hospital-scale Chest X-ray Database and Benchmarks on Weakly-Supervised Classification and Localization of Common Thorax Diseases.* IEEE CVPR 2017.

## 🚀 Running the Notebook

1. Download the ChestX-ray14 data (see the Dataset section above).
2. Install the requirements:

```bash
pip install pandas numpy torch torchvision transformers networkx scikit-learn matplotlib pillow jupyter
```

3. Open the notebook and update the data paths in the first cells:

```bash
jupyter notebook "image Vs CSV.ipynb"
```

A GPU is helpful for the image feature extraction step but is not required for the tabular pipeline.

## 📈 Results

The notebook contains the graph outputs for both pipelines. It shows how the tabular-only graph and the multimodal graph (with image features added) differ in structure and in the relationships they capture.

<!--
To make this section stronger, add:
1. A screenshot of a sample graph, saved as graph.png in this repo, then shown with: ![Sample knowledge graph](graph.png)
2. A small table comparing the two graphs (number of nodes, number of edges, node types, edge types)
3. Two or three lines on the main difference you observed between the two pipelines
-->

## ⚠️ Disclaimer

This project is for research and learning purposes only. It is **not** a medical tool and must not be used for diagnosis or clinical decisions.

## 🎓 Context

Developed as a Bioinformatics final-term project during the MS in Data Science program at the Institute of Management Sciences (IMSciences), Peshawar.

## 📄 License

This project is released under the [MIT License](LICENSE).

## 👤 Author

GitHub: [@mubashrazulphickar007-cpu](https://github.com/mubashrazulphickar007-cpu)
