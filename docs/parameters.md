# Parameters

The pipeline parameters are stored in the `pdp_config.yaml` file.
This file is divided in twelve sections:

* `input` stores the paths needed by the pipeline
* `parameters` stores parameters for the pipeline
* `ldsc`, `hdl` store parameters for global correlation methods
* `supergnova`, `hdl-l` store parameters for local correlation methods
* `factorgo`, `gfa`, `gleanr`, `guide` store parameters for latent factor analysis methods
* `assembly` stores parameters for the final loadings assembly
* `output` stores the directories in which to save the data/results.

The default parameters are those suggested in the corresponding articles.

## Number of factors

Unlike the other latent factor analysis methods, FactorGo and GUIDE do not automatically choose the number of factor to impute.
This number needs to be manually selected before running the pipeline.

!!! info
    To specify to number of factors, you can update the value of `factorgo/k_factors` and `guide/k_factors`.

## Masking the MHC region

Methods like FactorGo or GLEANR suggest using variants outside of the MHC region.
This region is located on chromosome 6, and we have provided the following range for *GRCh38*: 28510120-33480577.

!!! info
    To modify the range of the MHC region, please update the values of `parameters/mhc_start` and `parameters/mhc_end`.

## Including/Excluding specific methods

By default, we assume you will run every method that is available.
However, it is possible to specify which methods to run, as well as the methods for which you wish to assemble the results.

!!! info
    To specify which method to run, you can update the value of `include` for each method.
    To specify which method to assemble, you can update the `assembly` parameters.

## Computing results for a specific set of variants

Latent factor analysis methods will be run using the preprocessing filters suggested by each method in their respective article.
However, it is possible to estimate variant-factor associations for a new set of variants, different from the one used as input.

!!! info
    More information on the estimation of variant-factor associations can be found in the *[Assembling the results](assembling.md)* page.

Although the methods results will be computed for the input set, the assembled results will be computed for this new set, which will be common to all latent factor analysis methods.

!!! info
    To specify the list of variants to estimate the results for, you can update the value of `output_variants`.
