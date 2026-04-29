# Parameters

The pipeline parameters are stored in the `./config/` directory.
This directory contains 9 files:

* `pipeline_arguments.txt`, main parameters of the pipeline
* `assembly_arguments.txt`, parameters of the final assembly
* `{method}_arguments.txt`, parameters of each method (except LDSC)

!!! info
    The names of the files created during the pipeline depend on the parameters you have chosen.
    If it is different from the default, than it will change accordingly to differentiate this run from other runs.

Most parameters can be modified while some shouldn't to avoid breaking the pipeline.
This is specified by the use of the following dividing line:

```text
#=====================================DO NOT MODIFY AFTER THAT=====================================
```

## Masking the MHC region

Methods like FactorGo or GLEANR suggest using variants outside of the MHC region.
This region is located on chromosome 6, and we have provided the following range for *GRCh38*: 28510120-33480577.

!!! info
    To modify the range of the MHC region, please update the values of `mhc_start` and `mhc_end`.

## Using a pre-defined set of variants

By default, we will apply the preprocessing filters suggested by each method in their respective article.
However, it is also possible to provide a list of SNPs to analyze, so that every methods has the same input.

This list will replace the preprocessing steps for latent factors analysis methods (FactorGo, GFA, GLEANR, GUIDE), but not the global and local correlation methods (LDSC, HDL, SUPERGNOVA, HDL-L).

!!! info
    To indicate whether you want to apply the original filters or use a list of SNPs, you can update the value of `use_filters` in `./config/pipeline_arguments.txt`. To specify which list to use, you can update the value of `input_variants` in the same file.
