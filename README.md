# Gene Expression Analysis and Visualization

This project demonstrates a foundational **bioinformatics pipeline** for identifying and visualizing **differentially expressed genes (DEGs)** between two biological conditions using Python.  
This is a core skill set for processing transcriptomic data from platforms like **microarrays** or **RNA sequencing**.

---

## Project Goal

To perform **Differential Expression Analysis (DEA)** on simulated data, mimicking the structure of a public GEO dataset, and to visualize the results using industry-standard plots (**Volcano Plot** and **Heatmap**).

---

## Dataset Source

- **GEO Accession:** GSE68849 (Primary Breast Cancer vs. Normal Tissue)  
- **Data Used:** A synthetic dataset was generated in the script (`gene_expression_analysis.py`) to replicate the structure, sample groups (4 Control, 4 Disease), and expected differential expression patterns of the real GEO dataset.  

This allows the script to be run immediately in environments like **Google Colab** without complex data download steps.

---

## Analysis Methods & Technologies

The analysis pipeline adheres to standard best practices in gene expression analysis:

### 1. Data Wrangling & Quality Control
- **Library:** `pandas`  
- **Steps:**  
  - Loading expression data and phenotype information  
  - Ensuring data integrity (e.g., checking for null values)  
  - Splitting the data matrix into **Control** and **Disease** groups  

### 2. Differential Expression Analysis (DEA)
- **Libraries:** `pandas`, `numpy`, `scipy.stats`  
- **Log2 Fold Change (Log2FC):**
  \[
  \log_2 \left( \frac{\text{Mean Expression}_{\text{Disease}}}{\text{Mean Expression}_{\text{Control}}} \right)
  \]
- **Statistical Testing:**  
  Two-sample Welch’s T-test (`scipy.stats.ttest_ind` with `equal_var=False`) was used to determine the significance (p-value) of the difference between the two group means.  
- **Multiple Testing Correction:**  
  Bonferroni correction was applied to the raw p-values to control the False Discovery Rate (FDR).  
  The adjusted p-value (`adj_p_value`) is used for determining significance.

### 3. Visualization
- **Libraries:** `matplotlib.pyplot`, `seaborn`  
- **Volcano Plot:**  
  Plots **Log2FC (x-axis)** versus **−log₁₀(Adjusted P-value) (y-axis)**.  
  Genes passing the significance thresholds are colored **red**.  
- **Heatmap:**  
  Visualizes the **relative expression (Z-scores)** of the top 20 DEGs across all samples, demonstrating clear cluster separation between **Control** and **Disease** groups.

---

## Key Insights and Results

The **differentially expressed genes (DEGs)** were defined by the following criteria:

\[
|\text{Log2FC}| \geq 0.5
\]
\[
\text{Adjusted P-value} \leq 0.05
\]

| Regulation     | Key Simulated Gene | Real-World Biological Relevance |
|----------------|--------------------|----------------------------------|
| **Up-regulated** | `MYC`, `EGFR`       | Often oncogenes; their increased expression drives cell proliferation and is highly characteristic of many cancers. |
| **Down-regulated** | `BRCA1`             | A key tumor suppressor gene; reduced expression often leads to genomic instability and contributes to cancer development. |

The script successfully identified these genes as significant, validating the analysis pipeline.

---

## Skills Highlighted

- **pandas** (Data Wrangling)  
- **numpy** & **scipy** (Statistical Analysis)  
- **seaborn** & **matplotlib** (Data Visualization)  
- **Biological Interpretation**  
- **Reproducible Research** (GitHub Deployment)

---

