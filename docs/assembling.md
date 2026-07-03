# Assembling the results

The last step of the pipeline is to assemble of the results.
During this step, we will compile the results of each method into one single table where the rows are variants and columns are methods.

!!! note
    LDSC and HDL are not included in this final table seeing as the value would be the same accross all variants.

Since FactorGo, GFA and GLEANR have specific variant filtering in their preprocessing step, we fully join the results.
However, since GUIDE has none and we still want to avoid having a sparse assembled matrix, we will only keep GUIDE results for the variants used as input in the other methods.

For HDL-L and SUPERGNOVA, we will expand the local correlation from region to variant level in order to get a value for each variant previously selected.
