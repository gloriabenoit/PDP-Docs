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

## Additional files

Most methods need additional files to run.
Therefore, we have automated the download of each of these files to make sure everything runs smoothly.

```bash
sh ./src/get_files.sh
```

### Genome reference panel

This file should be a set of PLINK files, meaning `.bim`, `.bed` and `.fam` files.

!!! info
    To specify the reference panel to use, you can update the value of `ref_panel` in `./config/pipeline_arguments.txt`.

### HDL and HDL-L

HDL and HDL-L both use a pre-computed reference panel for the European-ancestry population.
Although it is possible to compute your own reference panel, we choose to use theirs and not `ref_panel`.

!!! note
    Please be aware that the pre-computed panels are quite heavy (33G for the global panel and ~2G for the local one).

!!! info
    To specify the reference panels for these methods, you can update the values of `global_panel_dir`, `local_panel_dir` and `local_bim_dir` in `./config/HDL_arguments.txt`.

### SUPERGNOVA

When reading the reference panel, SUPERGNOVA expects to find variants positions (in centimorgans).
Therefore, you need to make sure that you reference panel contains this information.

If not, SUPERGNOVA will crash, which is why we will extrapolate them with a [GRCh38 positions map](https://alkesgroup.broadinstitute.org/Eagle/downloads/tables/).

!!! info
    To indicate whether positions need to be extrapolated, you can update the value of `extrapolate_pos` in `./config/SUPERGNOVA_arguments.txt`.
    To specify which map to use, you can update the value of `pos_map` in the same file.
