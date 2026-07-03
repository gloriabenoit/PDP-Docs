# Running the pipeline


You can first do a dry run of the pipeline to make sure everything works with the following command:

```bash
snakemake -n -s pleiotropy_decomposition_pipeline.smk
```

If no error arises, then you can confidently run the pipeline with the `run_pdp.sh` script.

```bash
sh run_pdp.sh
```

!!! info
    Running each of the methods necessitates a number of intermediate files. We have marked those files as temporary, meaning they will be destroyed once the run is complete. However, you can keep them by adding the `--notemp` flag to the previous command.

    ```bash
    sh run_pdp.sh --notemp
    ```
