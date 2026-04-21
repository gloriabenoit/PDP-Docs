
# Methods dependencies
## Original Github repositories

Some methods need additionnal files to run, which are available on the original Github repositories.
We will clone each of them  since some are necessary but also as a way to give credit.

```bash
sh ./src/clone_repos.sh
```

## Package dependencies

!!! info
    More information on the specific dependencies can be found in the [*Implemented methods*](methods.md) page.

The methods have their own dependencies, therefore we will create a new virtual environment for each.

We will also create an environment for the pre- and post-processing done, using Python `3.13.2` and polars `1.39.3`.

```bash
sh ./src/dependencies/create_venv.sh
```

!!! note
    Please note that this step takes quite some time, thankfully you only need to do it once.
