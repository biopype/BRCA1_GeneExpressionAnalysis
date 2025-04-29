# BRCA1 Gene Expression Analysis in Breast Cancer

This project analyzes BRCA1 gene expression in breast tumor vs. normal breast tissue, with further stratification by metastasis status, using RNA-seq data (FPKM values) from the GEO dataset [GSE183947](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE183947).

## Objectives

- Compare BRCA1 expression between tumor and normal samples
- Assess expression differences by metastasis status
- Visualize expression patterns
- Perform statistical testing (Welch’s t-test, Mann-Whitney U)

## Dataset

- **Source:** GEO (GSE183947)
- **Samples:** 60 total (30 tumor, 30 normal)
- **Data type:** FPKM expression values for 20,246 genes

## Methods

- Data wrangling and merging of expression and metadata
- Descriptive statistics and distribution plots
- Hypothesis testing for differential expression
- Visualization: barplots, density plots, violin plots

## Key Findings

- BRCA1 shows higher mean expression in tumors, especially metastatic ones
- No statistically significant differences found (p > 0.05)
- Broad expression variability suggests complex regulation

## Limitations

- Small sample size
- Lack of clinical annotation
- Use of bulk RNA-seq data

## Future Work

- Larger cohorts and single-cell RNA-seq
- Integration of mutational, epigenetic, and proteomic data
- Correlation with treatment response

## Reference

Roy, R., Chun, J., & Powell, S. N. (2012). *BRCA1 and BRCA2: different roles in a common pathway of genome protection*. Nature Reviews Cancer, 12(1), 68–78. https://doi.org/10.1038/nrc3181
