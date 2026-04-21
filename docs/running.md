# Running the methods

The second step of the pipeline is to run the methods. During this step, we will run each methods independantly.

```bash
sh run_pipeline.sh
```

## Method specific properties

### HDL, SUPERGNOVA and HDL-L

Global and local genetic correlation methods compare pairs of studies.
Therefore, we automate them with a `sbatch` command allowing for parallel runs between each possible pairs.

### FactorGo and GUIDE

Unlike the other latent factor analysis methods, FactorGo and GUIDE do not automatically choose the number of factor to impute.
This number needs to be manually selected before running the pipeline.

!!! info
    To specify the number of factors to search for, you can update the value of `k` in `./config/FactorGo_arguments.txt` and `./config/GUIDE_arguments.txt`, for FactorGo and GUIDE respectively.
