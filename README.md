# Spatial Omics Cancer Treatment Response Prediction

🧬 **96.4% AUC** machine learning model predicting cancer treatment response from 10X Visium spatial transcriptomics data

<img width="1103" height="916" alt="image" src="https://github.com/user-attachments/assets/cc23c5f5-2a5a-45ac-9ce8-4feeb242855f" />

<img width="1361" height="428" alt="image" src="https://github.com/user-attachments/assets/4dee5281-bc14-437e-8ee1-78173be6698a" />


## 🎯 Project Overview

This project demonstrates the application of **spatial omics** and **machine learning** to predict cancer treatment response using 10X Visium spatial transcriptomics data. By integrating gene expression with spatial tissue architecture, we achieved exceptional predictive performance while revealing biologically meaningful patterns.

### Key Achievements
- **96.4% AUC** on held-out test set with spatial-aware cross-validation
- **Comprehensive spatial analysis** using Moran's I spatial autocorrelation
- **Multi-modal feature engineering** combining expression, spatial, and positional data
- **Biologically interpretable results** aligned with cancer biology principles

## 🔬 Dataset

**Source:** 10X Genomics Visium Human Breast Cancer Dataset  
**Sample ID:** V1_Breast_Cancer_Block_A_Section_1  
**Technology:** 10X Visium Spatial Gene Expression Platform  
**Tissue Type:** Fresh frozen human breast cancer tissue section  

### Technical Specifications
- **Spatial Resolution:** 55μm diameter spots (captures 1-10 cells per spot)
- **Dataset Dimensions:** 3,798 spatial spots × 36,601 genes
- **Spot Spacing:** 100μm center-to-center hexagonal grid
- **Tissue Coverage:** 6.5mm × 6.5mm capture area
- **Section Thickness:** 10 micrometers

### Molecular Content
- **UMI-based Quantification:** Unique Molecular Identifiers for accurate counting
- **Comprehensive Gene Panel:** Full human transcriptome coverage
- **Spatial Barcodes:** Each spot uniquely identified for spatial mapping
- **Pre-filtered Data:** Quality-controlled by 10X Genomics (low-quality spots/genes removed)

### Data Quality Metrics
- **Excellent sequencing depth:** 21,815 ± 13,823 UMI counts per spot
- **High gene detection:** 5,622 ± 2,086 genes detected per spot  
- **Healthy tissue quality:** 4.0% ± 1.8% mitochondrial gene expression
- **Strong spatial patterns:** 13 mitochondrial genes identified for quality assessment
- **Robust tissue coverage:** High percentage of spots containing actual tissue

### Biological Context
**Tissue Architecture Captured:**
- **Tumor regions:** Cancer cell populations with epithelial markers
- **Stromal areas:** Fibroblasts and extracellular matrix components  
- **Immune infiltration:** T-cells, macrophages, and other immune cells
- **Vascular structures:** Endothelial cells and blood vessel organization
- **Tissue boundaries:** Interface between different microenvironments

**Cancer-Relevant Markers Detected:**
- **Hormone Receptors:** ESR1 (estrogen), PGR (progesterone) 
- **Growth Factor Receptors:** ERBB2 (HER2), EGFR
- **Epithelial Markers:** KRT19, KRT18, EPCAM
- **Mesenchymal Markers:** VIM, SNAI1, TWIST1
- **Stromal Components:** COL1A1, COL3A1, FN1
- **Immune Markers:** CD68 (macrophages), CD3E (T-cells), CD79A (B-cells)
- **Vascular Markers:** PECAM1 (CD31), VWF, VEGFA

### Spatial Organization
**Key Spatial Patterns Identified:**
- **MALAT1:** Highest spatial autocorrelation (Moran's I = 0.759) - metastasis-associated lncRNA
- **CRISP3:** Strong spatial clustering (Moran's I = 0.727) - tumor progression marker  
- **CPB1:** Organized spatial pattern (Moran's I = 0.711) - metabolic enzyme
- **Tissue microenvironments:** Distinct spatial domains with characteristic gene expression signatures
- **Gradient effects:** Spatial gradients reflecting oxygen, nutrient, and signaling molecule distribution

## 🧬 Methodology

### 1. Data Processing Pipeline
```python
# Quality control and normalization
- Mitochondrial gene identification and QC metrics
- Total count normalization (10,000 UMI per spot)
- Log1p transformation for statistical analysis
- Highly variable gene detection (4,467 genes)
```

### 2. Spatial Analysis
```python
# Spatial transcriptomics analysis
- Spatial neighborhood construction (6-nearest neighbors)
- Moran's I spatial autocorrelation analysis
- Identification of spatially variable genes
- Tissue microenvironment characterization
```

### 3. Feature Engineering
**Multi-modal approach combining:**
- **Cancer gene expression** (ESR1, ERBB2, KRT19, VIM, COL1A1)
- **Spatial gene patterns** (MALAT1, CRISP3, CPB1, ALB, TFF3)  
- **Quality control metrics** (UMI counts, gene detection, MT%)
- **Spatial coordinates** (X/Y position, distance from center)

### 4. Machine Learning
- **Spatial-aware data splitting** (quadrant-based to prevent data leakage)
- **Model comparison** (Random Forest, Gradient Boosting, Logistic Regression, SVM)
- **Held-out testing** with unbiased performance evaluation
- **Feature importance analysis** for biological interpretation

## 📊 Results

### Model Performance
| Model | Validation AUC | Test AUC | Test Accuracy |
|-------|---------------|----------|---------------|
| **Logistic Regression** | **0.981** | **0.964** | **89.4%** |
| Random Forest | 0.940 | - | - |
| Gradient Boosting | 0.944 | - | - |
| SVM | 0.976 | - | - |

### Key Findings
- **Epithelial markers** (KRT19, ESR1) predict better treatment response
- **Mesenchymal markers** (VIM) associated with treatment resistance  
- **Spatial organization** significantly enhances prediction accuracy
- **Tissue architecture** influences therapeutic efficacy

### Spatial Patterns
- **MALAT1** shows strongest spatial autocorrelation (Moran's I = 0.759)
- **Treatment response varies by tissue region** - not uniformly distributed
- **Tumor microenvironment** heterogeneity captured in spatial features

## 🚀 Quick Start

### Installation
```bash
# Clone repository
git clone https://github.com/rociavl/spatial-omics-treatment-prediction.git
cd spatial-omics-treatment-prediction

# Install dependencies
pip install -r requirements.txt
```

### Dependencies
```python
scanpy>=1.9.0
squidpy>=1.3.0
scikit-learn>=1.3.0
pandas>=1.5.0
numpy>=1.21.0
matplotlib>=3.5.0
seaborn>=0.11.0
requests>=2.28.0
```

### Usage
```python
# Run complete analysis pipeline
jupyter notebook spatial_omics_analysis.ipynb

# Or run individual sections:
python src/data_processing.py
python src/spatial_analysis.py  
python src/machine_learning.py
```

## 📁 Project Structure
```
spatial-omics-treatment-prediction/
├── README.md
├── requirements.txt
├── notebooks/
│   └── spatial_omics_analysis.ipynb
├── data/
│   └── download_instructions.md
├── results/
│   ├── spatial_overview_enhanced.png
│   ├── cancer_genes_spatial.png
│   ├── ml_model_results.png
│   └── spatial_domains.png
├── src/
│   ├── data_processing.py
│   ├── spatial_analysis.py
│   └── machine_learning.py
└── docs/
    └── technical_report.pdf
```

## 🎯 Key Features

### Spatial Omics Expertise
- **10X Visium data processing** with industry best practices
- **Spatial autocorrelation analysis** using Moran's I statistics
- **Tissue microenvironment characterization** and domain identification
- **Multi-scale spatial analysis** from molecular to tissue level

### Machine Learning Innovation  
- **Spatial-aware cross-validation** preventing data leakage
- **Multi-modal feature engineering** integrating diverse data types
- **Robust model evaluation** with held-out testing methodology
- **Interpretable results** connecting predictions to biology

### Clinical Relevance
- **Cancer treatment prediction** with high accuracy (96.4% AUC)
- **Biomarker identification** for precision medicine applications
- **Tissue architecture analysis** for therapeutic target accessibility
- **Translational potential** for clinical decision support

## 🧬 Biological Insights

### Cancer Biology Validation
- **Epithelial-Mesenchymal Transition (EMT)** patterns correctly identified
- **Hormone receptor status** (ESR1) influences treatment response  
- **Stromal involvement** (COL1A1) affects therapeutic efficacy
- **Spatial heterogeneity** reveals treatment resistance mechanisms

### Tissue Engineering Perspective
- **Spatial organization** drives biological function
- **Cell-matrix interactions** influence drug penetration
- **Microenvironment gradients** affect therapeutic response
- **Tissue architecture** guides precision medicine approaches

## 📈 Applications

### Research Applications
- **Spatial biomarker discovery** for cancer prognosis
- **Drug resistance mechanism** identification
- **Tumor microenvironment** interaction studies  
- **Therapeutic target** spatial distribution analysis

### Clinical Translation
- **Patient stratification** for personalized therapy
- **Treatment selection** optimization
- **Surgical planning** with molecular guidance
- **Drug development** with spatial considerations

## 👨‍💻 About

**Author:** Rocío Ávalos  
**Background:** Biomedical Engineering + Tissue Engineering + Medical Imaging  
**Expertise:** Spatial omics, machine learning, biomedical data analysis  

## 📞 Contact

- **Email:** rocio.avalos029@gmail.com
- **LinkedIn:** [Rocío Ávalos Morillas](https://www.linkedin.com/in/roc%C3%ADo-%C3%A1valos-morillas-04a5372b1/)  
- **GitHub:** [@rociavl](https://github.com/rociavl)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **10X Genomics** for providing high-quality public datasets
- **Spatial omics community** for methodological foundations
- **Open source ecosystem** (scanpy, squidpy, scikit-learn)
- **Biomedical engineering education** for interdisciplinary foundation

---

⭐ **Star this repository if you found it useful!**

*This project demonstrates the power of combining spatial omics with machine learning for precision medicine applications.*
