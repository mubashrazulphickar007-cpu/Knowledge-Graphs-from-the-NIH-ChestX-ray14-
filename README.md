# Knowledge-Graphs-from-the-NIH-ChestX-ray14-
# Knowledge Graphs from the NIH ChestX-ray14 Dataset

A knowledge graph construction pipeline built on the NIH ChestX-ray14 dataset, combining tabular metadata and image-derived features to represent relationships between patients, findings, and diagnostic labels.

## 🎯 Project Overview

Chest X-ray datasets contain rich information across two modalities: structured tabular metadata (patient demographics, disease labels, view position) and the raw images themselves. This project builds a **dual-pipeline** approach to compare how knowledge graphs constructed from each modality differ, and to explore combining them into a richer multimodal representation.

## 🧪 Methodology

Two parallel pipelines are implemented and compared:

1. **CSV/Tabular pipeline** — builds graph entities and relations directly from the structured metadata (patient ID, findings, follow-up visits, demographics).
2. **Direct multimodal pipeline** — extracts image-level features using pretrained CNN and transformer backbones (**ResNet**, **DenseNet**, **ViT**, **CLIP**) and incorporates them as graph node features alongside the tabular data.

A **patient-disjoint split** is enforced throughout, ensuring no patient's images appear in both training and evaluation subsets — this avoids data leakage that patient-level correlation could otherwise introduce.

## 📁 Repository Structure

```
.
├── image Vs CSV.ipynb     # Dual-pipeline notebook: tabular vs. image-based KG construction
└── README.md
```

*(Suggested: rename `image Vs CSV.ipynb` to something like `dual_pipeline_tabular_vs_imaging.ipynb` for clarity.)*

## 🚀 Running the Notebook

```
pip install pandas numpy torch torchvision transformers networkx scikit-learn
jupyter notebook "image Vs CSV.ipynb"
```

## 📊 Key Components

- Pretrained feature extraction using ResNet, DenseNet, ViT, and CLIP backbones
- Patient-disjoint dataset construction to prevent leakage
- Knowledge graph assembly linking patients, findings, and extracted features
- Comparative analysis between tabular-only and multimodal graph representations

## 📈 Results

*(Add: a sample graph visualization, and a comparison of how well each pipeline's graph captures known disease co-occurrence patterns or supports downstream classification.)*

## 🎓 Context

This project was developed as a Bioinformatics final-term deliverable during a Data Science MS program (IMSciences, Peshawar), with a companion knowledge graph extension explored on TCGA data using similar CNN-based feature extraction.

## 📄 License

Educational/academic use.
