# Gene Expression Analysis of BRCA1 in Breast Cancer

## Abstract

This study analyzed BRCA1 gene expression patterns in breast tumor versus normal breast tissue samples, with additional stratification by metastasis status. Using FPKM values from 60 samples (30 tumor, 30 normal) from GEO dataset GSE183947, we performed descriptive statistics, visualization, and hypothesis testing. While BRCA1 showed higher mean expression in tumor samples (especially metastatic ones), neither t-tests nor Mann-Whitney U tests revealed statistically significant differences between tissue types (p=0.1999 and p=0.3403 respectively). The density plots revealed right-skewed distributions with tumor samples showing a broader expression range. These findings suggest complex regulation of BRCA1 in breast cancer that may not be captured by bulk expression differences alone.

## Introduction

BRCA1 is a critical tumor suppressor gene involved in DNA repair, with germline mutations conferring high lifetime risk of breast and ovarian cancers (Roy et al., 2012). While mutational status is well-characterized, the role of BRCA1 expression levels in tumor progression remains debated. This analysis examines:

- BRCA1 expression differences between tumor and normal breast tissues  
- Expression variation by metastasis status  
- Distribution patterns across samples  

The clinical relevance stems from BRCA1's role in treatment response - tumors with homologous recombination deficiency (often BRCA1-related) may respond differently to platinum drugs and PARP inhibitors.

## Methodology

### Data Acquisition and Preprocessing

- **Library Installation**: Essential Python packages (pandas, seaborn, matplotlib, GEOparse) were loaded for data manipulation and visualization.  
- **Data Loading**:  
  - Expression data was loaded from "GSE183947_fpkm.csv" containing FPKM values for 20,246 genes across 60 samples (20246×61 dataframe).  
  - Metadata was retrieved from GEO (GSE183947) using GEOparse, containing sample characteristics.  
- **Data Wrangling**:  
  - Metadata was processed to extract tissue type (tumor/normal) and metastasis status (yes/no).  
  - Expression data was transformed from wide to long format (1,214,760 rows) for analysis.  
  - Final merged dataset combined expression values with sample metadata.

### Analytical Approach

- **Descriptive Statistics**: Calculated mean, median and standard deviation of BRCA1 FPKM values grouped by tissue type and metastasis status.  
- **Visualization**:  
  - **Barplot**: BRCA1 expression across all samples colored by tissue type  
  - **Density plot**: Distribution comparison between tissue types  
  - **Violin plot**: Expression by metastasis status  
- **Statistical Testing**:  
  - **Welch's t-test** (accounts for unequal variances)  
  - **Mann-Whitney U test** (non-parametric alternative)  

## Results

### Descriptive Statistics

| Gene  | Tissue | Metastasis | Mean FPKM | Median FPKM | Std Dev |
|-------|--------|------------|-----------|-------------|---------|
| BRCA1 | Tumor  | No         | 7.58      | 6.63        | 3.63    |
| BRCA1 | Tumor  | Yes        | 12.58     | 8.87        | 11.31   |
| BRCA1 | Normal | No         | 6.29      | 5.52        | 3.05    |
| BRCA1 | Normal | Yes        | 9.11      | 7.86        | 5.76    |

**Key observations:**
- Highest mean expression in metastatic tumors (12.58 FPKM)  
- Normal tissues showed more consistent expression (lower std dev)  
- Non-metastatic tumors had expression similar to normal tissue  

### Visualizations

![image](https://github.com/user-attachments/assets/344f8957-657b-4691-a345-c22752bed2b3)

**Barplot (Fig 1):**
- Showed substantial variability in BRCA1 expression across samples  
- No clear visual separation between tumor and normal groups  
- Several tumor samples showed exceptionally high expression (>30 FPKM)  

![image](https://github.com/user-attachments/assets/c1f8e8b0-f0e5-4329-afe7-4f074420e5fe)

**Density Plot (Fig 2):**
- Both distributions right-skewed  
- Tumor samples showed broader distribution (especially right tail)  
- Normal tissue distribution more concentrated around 5-10 FPKM  

![image](https://github.com/user-attachments/assets/e5598e6e-11f4-4b96-b28b-999cd07f079f)

**Violin Plot (Fig 3):**
- Metastasis-positive samples showed higher median expression  
- Wider interquartile range in metastasis-positive group  
- Several high-expression outliers in both groups  

### Statistical Tests

**Welch's t-test:**
- t-statistic = 1.301  
- p-value = 0.1999  
- Failed to reject null hypothesis (no significant difference)  

**Mann-Whitney U:**
- U-statistic = 515  
- p-value = 0.3403  
- Confirmed non-significant difference in distributions  

## Discussion

The analysis reveals several important insights:

### Expression Trends:

While not statistically significant, the consistent pattern of higher BRCA1 expression in tumors (especially metastatic) suggests potential biological relevance. The large standard deviations indicate substantial heterogeneity that may obscure group differences.

### Technical Considerations:

The use of FPKM (rather than TPM) for normalization and potential batch effects could influence results. The presence of extreme outliers suggests possible technical artifacts or biological extremes.

### Biological Implications:

The maintained (even elevated) BRCA1 expression in tumors argues against simple loss-of-function through reduced expression. Alternative mechanisms like:  
- Post-translational modification  
- Dominant-negative mutants  
- Epigenetic silencing in subpopulations  

may be more relevant than bulk expression changes.

### Clinical Correlation:

The higher expression in metastatic samples aligns with some reports linking BRCA1 overexpression to aggressive phenotypes, though causation remains unclear.

## Limitations

- Small sample size (n=30 per group) limits statistical power  
- Lack of clinical annotations (grade, subtype, treatment history)  
- Bulk RNA-seq masks tumor heterogeneity  
- Unknown impact of tumor cellularity differences  

## Conclusion

This comprehensive analysis found no statistically significant difference in BRCA1 expression between breast tumor and normal tissue at bulk level, despite suggestive trends. The substantial variability within groups and pattern of higher expression in metastatic samples warrants further investigation with:  
- Larger cohorts  
- Single-cell approaches  
- Proteomic validation  
- Functional assays  

The findings caution against simplistic assumptions about BRCA1's role based solely on expression levels, highlighting the need for multi-omics integration in understanding its complex biology in breast cancer.

## Future Directions

- Analyze BRCA1 co-expression networks  
- Incorporate mutational status data  
- Examine alternative splicing isoforms  
- Integrate with DNA methylation data  
- Compare with treatment response outcomes  

This work provides a foundation for more nuanced investigations of BRCA1 regulation in breast cancer progression and therapy resistance.

## References:

Roy, R., Chun, J., & Powell, S. N. (2012). BRCA1 and BRCA2: different roles in a common pathway of genome protection. *Nature Reviews Cancer*, 12(1), 68–78. doi: 10.1038/nrc3181.
