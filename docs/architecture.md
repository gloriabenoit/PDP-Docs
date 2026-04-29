# Repertory architecture

Once you have downloaded every necessary file, and ran at least one analysis, your repertory should look something like this:

```text
├── config
├── data
├── env
├── log
├── module
├── res
└── src
```

## *config* directory

This directory stores `.txt` files containing the pipeline's parameters.

!!! info
    More information on the possible parameters can be found in the [*Parameters*](parameters.md) pages.

## *data* directory

This directory stores every needed files to run each method.
It is created during the preprocessing step and contains one directory per method.

## *env* directory

This directory stores every virtual environnment needed for each method.
The Python environment are actual virtual environnment while the R ones are actually the paths to `R_LIBS_USER`.

!!! info
    More information on the cloning of these repositories can be found in the [*Dependencies*](dependencies.md#packages) pages.

## *log* directory

This directory stores the log of every method ran.
To make it easier to navigate, it contains a directory per pipeline run, then one per method.

## *module* directory

This directory stores the original Github repositories of each method.
It is created before running your first analysis.

!!! info
    More information on the cloning of these repositories can be found in the [*Dependencies*](dependencies.md#github-repositories) pages.

## *res* directory

This directory stores the results of every method ran.
To make it easier to navigate, it contains a directory per pipeline run, then one per method.

## *src* directory

This directory stores the necessary code to each method, thus the entire pipeline.
