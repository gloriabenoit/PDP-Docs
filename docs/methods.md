# Implemented methods

The following page lists all methods and their necessary packages.

!!! info
    The download of each package is automated in a single script, as explained in the [*Dependencies*](dependencies.md) page.

## Global genetic correlation

### LDSC

!!! reference
    Bulik-Sullivan, Brendan K et al. “LD Score regression distinguishes confounding from polygenicity in genome-wide association studies.” Nature genetics vol. 47,3 (2015): 291-5. doi:10.1038/ng.3211

LD Score Regression (LDSC) quantifies the contribution of true polygenic signal and bias by examining the relationship between test statistics and linkage disequilibrium (LD).

LDSC is available as a Python package. However, we are using version `1.0.1` as a container when running the JASS pipeline.

!!! warning
    LDSC needs to be run before running the pipeline, at the same time as the data preprocessing in the JASS pipeline.
    Please make sure that `params.compute_LDSC_matrix` in the `jass_pipeline.nf` file is set to `true`, in order to run LDSC during this step.

### HDL

!!! reference
    Ning, Zheng et al. “High-definition likelihood inference of genetic correlations across human complex traits.” Nature genetics vol. 52,8 (2020): 859-864. doi:10.1038/s41588-020-0653-y

High-Definition Likelihood (HDL) is a likelihood-based method for estimating genetic correlation using GWAS summary statistics.

HDL is available as a R package. We are using R `4.4.0` and the following dependencies:

| Package    | Version  | Available on |
|------------|----------|--------------|
| data.table | 1.18.2.1 | CRAN         |
| doSNOW     | 1.0.20   | CRAN         |
| dplyr      | 1.1.4    | CRAN         |
| HDL        | 1.4.1    | Github       |

## Local genetic correlation

### SUPERGNOVA

!!! reference
    Zhang, Yiliang et al. “SUPERGNOVA: local genetic correlation analysis reveals heterogeneous etiologic sharing of complex traits.” Genome biology vol. 22,1 262. 7 Sep. 2021, doi:10.1186/s13059-021-02478-w

SUPER GeNetic cOVariance Analyzer (SUPERGNOVA) is a statistical framework to perform local genetic covariance analysis.

SUPERGNOVA is available as a Python package. We are using Python `3.8.18` and the following dependencies:

| Package      | Version |
|--------------|---------|
| bitarray     | 2.9.2   |
| numpy        | 1.19.5  |
| pandas       | 0.25.3  |
| scikit-learn | 0.24.2  |
| scipy        | 1.5.3   |

### HDL-L

!!! reference
    Li, Yuying et al. “An enhanced framework for local genetic correlation analysis.” Nature genetics vol. 57,4 (2025): 1053-1058. doi:10.1038/s41588-025-02123-3

HDL-L is the local version of high-definition likelihood ([HDL](#hdl)). It is specifically tailored for local heritability and genetic correlation analysis using GWAS summary statistics.

Like HDL, HDL-L is available as a R package, with the same dependencies.

## Latent factor analysis

### FactorGo

!!! reference
    Zhang, Zixuan et al. “A scalable approach to characterize pleiotropy across thousands of human diseases and complex traits using GWAS summary statistics.” American journal of human genetics vol. 110,11 (2023): 1863-1874. doi:10.1016/j.ajhg.2023.09.015

Factor analysis model in Genetic assOciation (FactorGo) is a scalable variational factor analysis model that learns pleiotropic factors using GWAS summary statistics.

FactorGo is available as a Python package. We are using Python `3.13.2` and the following dependencies:

| Package | Version |
|---------|---------|
| jax     | 0.9.1   |
| jaxlib  | 0.9.1   |
| numpy   | 2.4.3   |
| pandas  | 3.0.1   |

### GFA

!!! reference
    Morrison, Jean et al. “Genetic Factor Analysis for Characterizing Phenome-Wide Patterns of Genetic Pleiotropy.” Under Revision at Nature Genetics (July 2024). doi:/10.21203/rs.3.rs-4714610/v1 Preprint.

Genetic Factor Analysis (GFA) uses factor analysis to identify common genetic factors shared by multiple traits.

GFA is available as a R package. We are using R `4.4.0` and the following dependencies:

| Package           | Version    | Available on |
|-------------------|------------|--------------|
| VariantAnnotation | 1.52.0     | Bioconductor |
| BiocManager       | 1.30.27    | CRAN         |
| dplyr             | 1.2.0      | CRAN         |
| ggrepel           | 0.9.6      | CRAN         |
| purrr             | 1.2.1      | CRAN         |
| readr             | 2.2.0      | CRAN         |
| rlang             | 1.1.6      | CRAN         |
| stringr           | 1.6.0      | CRAN         |
| GFA               | 1.0.0.449  | Github       |
| gwasvcf           | 0.1.5      | Github       |
| ieugwasr          | 1.1.0.9000 | Github       |

### GLEANR

!!! reference
    Omdahl, Ashton R et al. “Sparse matrix factorization robust to sample sharing across GWASs reveals interpretable genetic components.” American journal of human genetics vol. 112,9 (2025): 2178-2197. doi:10.1016/j.ajhg.2025.07.003

GWAS Latent Embeddings Accounting for Noise and Regularization (GLEANR) is a GWAS matrix factorization tool to estimate sparse latent pleiotropic genetic factors.

GLEANR is available as a R package. We are using R `4.4.0` and the following dependencies:

| Package    | Version    | Available on |
|------------|------------|--------------|
| data.table | 1.18.2.1   | CRAN         |
| gleanr     | 0.0.0.9000 | Github       |

### GUIDE

!!! reference
    Lazarev, Daniel et al. “GUIDE deconstructs genetic architectures using association studies.” bioRxiv : the preprint server for biology 2024.05.03.592285. 8 Apr. 2025, doi:10.1101/2024.05.03.592285. Preprint.

Genomic Unmixing by Independent Decomposition (GUIDE) estimates a set of statistically independent latent factors that best express the patterns of association across many traits.

GUIDE is available as a Python package. We are using Python `3.13.2` and the following dependencies:

| Package      | Version |
|--------------|---------|
| numpy        | 1.18.5  |
| polars       | 1.38.1  |
| scipy        | 1.5.0   |
| scikit-learn | 0.23.1  |
