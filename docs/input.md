# Input data

The pipeline takes as input univariate GWAS summary statistics.
To ease the running of our pipeline, the data first needs to go through another pipeline: the JASS analysis pipeline.

## JASS (Julienne et al. 2020)

!!! reference
    Julienne, Hanna et al. “JASS: command line and web interface for the joint analysis of GWAS results.” NAR genomics and bioinformatics vol. 2,1 (2020): lqaa003. doi:10.1093/nargab/lqaa003

The starting point of our pipeline is the output of the JASS analysis pipeline, which is described in great detail in the [official page](https://gitlab.pasteur.fr/statistical-genetics/jass_suite_pipeline). The JASS analysis pipeline is a way for us to correctly format GWAS summary statistics as well as run LDSC on the data.

!!! warning
    Please make sure that `params.compute_LDSC_matrix` in the `jass_pipeline.nf` file is set to `true`, in order to run LDSC.

Putting the input data through the JASS analysis pipeline allows for the following QC and preprocessing steps:

* Select variants found in the input reference panel (MAF > 0.01)
* Align coded allele with the reference panel (updating variant information accordingly)
* Infer variant sample size if not present (from MAF, standard deviation and genetic effect)
* Remove variants with heterogeneous sample sizes
* Normalize the effect size to Z-scores

## Set of studies

In addition to the harmonized summary statistics obtained with JASS, you need a `.txt` file specifying the studies for which you would like to run the pipeline.
This file should contain one study per line, without the file extension.

!!! note
    For instance, for the outcome `BREAST-CANCER` in the consortium `BCAC`, the JASS harmonized file will be `z_BCAC_BREAST-CANCER.txt`.
    Therefore, you should only write `z_BCAC_BREAST-CANCER`.

## Additional files

### Genome reference panel

This file should be a set of PLINK files, meaning `.bim`, `.bed` and `.fam` files.

!!! info
    To specify the reference panel to use, you can update the value of `input/ref_panel` in `pdp_config.yaml`.

### HDL and HDL-L

HDL and HDL-L both use a pre-computed reference panel for the European-ancestry population.
Although it is possible to compute your own reference panel, we choose to use theirs and not `input/ref_panel`.

The reference panel for HDL is available on [Dropbox](https://www.dropbox.com/s/6js1dzy4tkc3gac/UKB_imputed_SVD_eigen99_extraction.tar.gz?dl=0), and the ones for HDL-L are available on [Zenodo](https://zenodo.org/records/14825987).

!!! note
    Please be aware that the pre-computed panels are quite heavy (33G for HDL and 30G for HDL-L).

You can use the following helper scripts to easily download the reference panels.

```bash
sh src/helper/get_hdl_ref.sh
sh src/helper/get_hdl-l_ref.sh
```

!!! info
    To specify the reference panels for these methods, you can update the values of `hdl/global_panel`, `hdl-l/local_panel` and `hdl-l/local_bim` in `pdp_config.yaml`.

### SUPERGNOVA

#### Region partitions

In order to unify the results for the local correlation methods, SUPERGNOVA will use the same partition as HDL-L.
Since this information is stored in a `.R` file, we need to extract it before correctly formatting it to be used with SUPERGNOVA.

```bash
# Download and format the partition
sh src/helper/get_partition.sh \
    data/HDL-L/LD \ # Local reference panel
    data/HDL-L/HDL-L_regions.csv \ # HDL-L partition output
    data/SUPERGNOVA/partition/HDL-L_regions.@.tsv # SUPERGNOVA partition output
```

#### Variant positions

When reading the reference panel, SUPERGNOVA expects to find variants positions (in centimorgans). If not, SUPERGNOVA will run indefinitely.
Therefore, you need to make sure that you reference panel contains this information.

You can use the following helper scripts to download a [GRCh38 positions map](https://alkesgroup.broadinstitute.org/Eagle/downloads/tables/) and use it to extrapolate variant positions for your reference panel.

```bash
# Download the genetic map
sh src/helper/get_hg38_map.sh

# Extrapolate positions
sh src/helper/add_bim_positions.sh \
    /pasteur/helix/projects/GGS_WKD/DATA_1000G/Panels/EUR/All_ensemble_1000G_hg38_EUR_all_chr \ # Input reference panel
    data/SUPERGNOVA/genetic_map_hg38_withX.txt.gz \ # Genetic map
    data/All_ensemble_1000G_hg38_EUR_all_chr # Output reference panel
```
