# Parameters

The pipeline parameters are stored in the `./config/` directory.
This directory contains 9 files:

* `pipeline_arguments.txt`, main parameters of the pipeline
* `assembly_arguments.txt`, parameters of the final assembly
* `{method}_arguments.txt`, parameters of each method (except LDSC)

!!! info
    The names of the files created during the pipeline depend on the parameters you have chosen.
    If it is different from the default, than it will change accordingly to differentiate this run from other runs.

Most parameters can be modified while other shouldn't to avoid breaking the pipeline.
This is specified by the use of the following dividing line:

```text
#=====================================DO NOT MODIFY AFTER THAT=====================================
```
