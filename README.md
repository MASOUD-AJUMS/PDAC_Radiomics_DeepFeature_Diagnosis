# Tumor Echoes in Healthy Zones: A Radiomic Perspective on Pancreatic Ductal Adenocarcinoma Diagnosis

This repository contains the datasets and source code for the study:

**"Tumor Echoes in Healthy Zones: A Radiomic Perspective on Pancreatic Ductal Adenocarcinoma Diagnosis"**

The project explores a novel approach to diagnose Pancreatic Ductal Adenocarcinoma (PDAC) using radiomic and deep learning features extracted not from the tumor itself, but from non-tumorous anatomical structures in contrast-enhanced CT scans.

---

## 🧠 Abstract (Structured)

**Objective:**  
To overcome limitations of tumor-centric imaging by identifying malignancy-induced changes in nearby healthy anatomical structures through systemic feature extraction and multi-region analysis.

**Materials and Methods:**  
- Dataset: 1,263 patients (PDAC and non-PDAC)  
- Structures: arteries, veins, pancreatic duct, parenchyma, and common bile duct  
- Features:  
  - **Radiomics** (via PyRadiomics, 107 features/region)  
  - **Deep Learning** (via 3D Convolutional Autoencoder)  
- Three Approaches:  
  1. Healthy tissue only (per-label)  
  2. Row-wise label fusion (Approach 2)  
  3. Column-wise patient fusion (Approach 3)  
- Feature selection + machine learning classification with explainability via SHAP and t-SNE.

**Results:**  
- Best accuracy in Approach 3 (F1-score: 88.33%, AUC: 97.98%)  
- Radiomic features outperformed deep features overall  
- Pancreatic duct & parenchyma most informative  
- SHAP/t-SNE confirmed diagnostic relevance of healthy tissues

**Conclusion:**  
Systemic changes in non-tumorous tissues offer early, interpretable diagnostic power for PDAC detection, especially in radiologically occult cases.

---

## 📁 Folder Structure

PDAC_Radiomics_DeepFeature_Diagnosis/
│
├── data/
│   ├── radiomics/
│   │   ├── step_1/      # Individual healthy regions
│   │   ├── step_2/      # Row-wise label fusion (Approach 2)
│   │   └── step_3/      # Column-wise patient fusion (Approach 3)
│   ├── deep_features/
│   │   ├── step_1/
│   │   ├── step_2/
│   │   └── step_3/
│   └── *.xlsx           # All feature tables (per label & approach)
│
├── code/
│   ├── feature_extraction/
│   │   ├── radiomics-extract.ipynb
│   │   └── deep-feature-extract.ipynb
│   ├── models/
│   │   └── model_pipeline.py
│   └── visualization/
│       ├── SHAP.ipynb
│       ├── t-SNE.ipynb
│       └── Heat map code.ipynb
└── README.md

---

## 🧪 Feature Extraction Modules

### 🔸 Radiomics
Extracted using PyRadiomics from segmented anatomical structures. Features include intensity, texture, and shape characteristics. Available in:
```
data/radiomics/
```

### 🔸 Deep Learning
Extracted using a custom-trained 3D convolutional autoencoder on cropped anatomical patches (from NIfTI format). Output bottleneck vectors represent learned features per region:
```
data/deep_features/
```

---

## 🤖 Machine Learning Pipeline

### `model_pipeline.py` Includes:
- Feature selection: `VarianceThreshold`, `SelectKBest`, `RandomForest`, etc.
- Classifiers: `LightGBM`, `XGBoost`, `CatBoost`, `MLP`, `AdaBoost`, etc.
- Ensemble strategies: Voting and stacking
- Balancing classes using SMOTE
- Visual outputs: ROC, confusion matrix, classification report
- Metrics saved for comparison

---

## 📊 Visualization Notebooks

| Notebook              | Purpose                                              |
|-----------------------|------------------------------------------------------|
| `SHAP.ipynb`          | Feature importance & explainability                 |
| `t-SNE.ipynb`         | 2D visualization of feature clusters                 |
| `Heat map code.ipynb` | Compare model performance with a heatmap            |

---

## 🚀 Results Summary

- Best results with **LightGBM + VarianceThreshold**
- F1-score: **88.33%**
- AUC: **97.98%**
- Radiomic features > Deep features
- Pancreatic duct & parenchyma: most discriminative


---

## 📬 Contact

For questions, feedback or collaboration:
📧 [masoudrezayi1398@gmail.com]  
🧠 GitHub Issues: [Open an issue](https://github.com/MASOUD-AJUMS/PDAC_Radiomics_DeepFeature_Diagnosis/issues)

---

🔬 Let's decode what tumors whisper into their surroundings.
