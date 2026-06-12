# Assembling the results

The third and last step of the pipeline is to assemble of the results.
During this step, we will compile the results of each method into one single table where the rows are variants and columns are methods.

```bash
sh run_assembly.sh
```

!!! note
    During the assembly HDL, SUPERGNOVA and HDL-L results are summarized into one file each to make it easier to take a look at the results.

Since FactorGo, GFA and GLEANR have specific variant filtering in their preprocessing step, we fully join the results.
However, since GUIDE has none and we still want to avoid having a sparse assembled matrix, we will only keep GUIDE results for the variants used as input in the other methods.

For HDL-L and SUPERGNOVA, we will expand the local correlation from region to variant level in order to get a value for each variant previously selected.
