
# Dependencies
## Github repositories

Some methods need additionnal files to run, which are available on the original Github repositories.
We will clone each of them  since some are necessary but also as a way to give credit.

```bash
sh src/helper/clone_repos.sh
```

## Packages

The methods have their own dependencies, therefore we need a new virtual environment for each.
Additionnaly, you need an environment for the pre- and post-processing done, using Python `3.13.2` and polars `1.39.3`.

These environments should be stored in the `env/` directory, and should be named depending on the method:

* HDL and HDL-L packages should be downloaded in `env/hdl`
* SUPERGNOVA packages should be downloaded in `env/supergnova`
* FactorGo packages should be downloaded in `env/factorgo`
* GFA packages should be downloaded in `env/gfa`
* GLEANR packages should be downloaded in `env/gleanr`
* GUIDE packages should be downloaded in `env/guide`
* Pre- and post-processing packages should be downloaded in `env/processing`

!!! info
    More information on the specific packages and their versions can be found in the [*Implemented methods*](methods.md) page.

You can use the following script to easily create all needed virtual environments.

```bash
sh src/helper/create_venv.sh
```
