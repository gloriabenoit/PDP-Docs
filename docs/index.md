# Pleiotropy Decomposition Pipeline using GWAS summary statistics

## Architecture

![Pipeline architecture](./img/pipeline_architecture.png)

This pipeline will compute results for a total of **8 methods**:

* **Global correlation methods:**
    * LDSC ([Bulik-Sullivan et al. 2015](https://pubmed.ncbi.nlm.nih.gov/25642630/), [Github repo](https://github.com/bulik/ldsc))
    * HDL ([Ning et al. 2020](https://pubmed.ncbi.nlm.nih.gov/32601477/), [Github repo](https://github.com/zhenin/HDL))
* **Local correlation methods:**
    * SUPERGNOVA ([Zhang et al. 2021](https://pubmed.ncbi.nlm.nih.gov/34493297/), [Github repo](https://github.com/qlu-lab/SUPERGNOVA))
    * HDL-L ([Li et al. 2025](https://pubmed.ncbi.nlm.nih.gov/40065165/), [Github repo](https://github.com/zhenin/HDL))
* **Latent factor analysis methods:**
    * FactorGo ([Zhang et al. 2023](https://pubmed.ncbi.nlm.nih.gov/37879338/), [Github repo](https://github.com/mancusolab/FactorGo))
    * GFA ([Morrison et al. Preprint](https://www.researchsquare.com/article/rs-4714610/v1), [Github repo](https://github.com/jean997/GFA))
    * GLEANR  ([Omdahl et al. 2025](https://pubmed.ncbi.nlm.nih.gov/40730164/), [Github repo](https://github.com/aomdahl/gleanr))
    * GUIDE ([Lazarev et al. Preprint](https://pubmed.ncbi.nlm.nih.gov/38766146/), [Github repo](https://github.com/daniel-lazarev/GUIDE))

## Installation

```bash
# Download with https
git clone https://github.com/gloriabenoit/pleiotropy_decomposition.git
# or ssh
git clone git@github.com:gloriabenoit/pleiotropy_decomposition.git

cd pleiotropy_decomposition
```

## How to use
### Input

The pipeline takes as input GWAS summary statistics that have been passed through the [JASS analysis pipeline](https://gitlab.pasteur.fr/statistical-genetics/jass_suite_pipeline), to harmonize your GWAS summary statistics formats as well as run LDSC.
The output folder of this pipeline is the main input of ours.

### Parameters

You can alter the parameters of the pipeline as well as the methods by changing the values of the `{step}_arguments.txt` files in the `./config/` folder.

By default, we will apply the preprocessing filters suggested in each article.
However, it is also possible to provide a list of SNPs to analyze, so that every methods has the same input.
This list will replace the preprocessing steps for latent factors analysis methods (FactorGo, GFA, GLEANR, GUIDE), but not the global and local correlation methods (LDSC, HDL, SUPERGNOVA, HDL-L).

!!! info
    To indicate whether you want to apply the original filters or use a list of SNPs, you can update the value of `use_filters` in `./config/pipeline_arguments.txt`.

### Running

The three steps of our pipeline can be run separately.

```bash
sh run_preprocessing.sh
sh run_pipeline.sh
sh run_assembly.sh
```

!!! warning
    As of now, the steps need to be launched manually one after the other once they're complete.
