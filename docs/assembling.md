# Assembling the results

The last step of the pipeline is to assemble of the results.
During this step, we will compile the results of each method into one single table where the rows are variants and columns are methods.

!!! note
    LDSC and HDL are not included in this final table seeing as the value would be the same accross all variants.

As previously mentioned, input sets of variants vary across latent factor analysis method.
However, it is possible to estimate variant-factor associations for a new set of variants using generalized least squares (GLS).

Considering $n$ the number of variants, $m$ the number of traits and $k$ the number of factors, each latent factor analysis method will produce two main files:

* **Trait loadings ($\hat{T}$)**: Trait-factor association, a matrix of size $m \times k$
* **Variant loadings ($\hat{V}$)**: Variant-factor association, a matrix of size $n \times k$

Thus, the formula to compute GLS estimates is as follows:

$$
 \hat{V}_i = (\hat{T}^\top \Sigma^{-1} \hat{T})^{-1} (\hat{T}^\top \Sigma^{-1} \hat{\beta}_i)
$$

where $\hat{V}_i$ is a vector of size $1 \times k$ of estimated variant loadings for variant $i$, $\Sigma$ is a matrix of size $m \times m$ of LDSC intercepts and $\hat{\beta}_i$ is a vector of size $1 \times m$ of observed effects of variant $i$ on $m$ traits (GWAS summary statistics).

We will use this in order to assemble results over the same set of variants for all methods.
This common set of variants is defined as all variants included in FactorGo, GFA or GLEANR preprocessing.
Since GUIDE does not filter variants, we will already have variant loadings for this set.

!!! info
    It is also possible to specify a different set of variants to use in the assembly.
    More information on this can be found in the *[Parameters](parameters.md)* page.
