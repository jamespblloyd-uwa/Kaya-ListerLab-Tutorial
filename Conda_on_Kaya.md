# Using conda to manage packages and environments on Kaya 

This tutorial gives you an introdcution to using `conda` (and `mamba`) on the `Kaya` server at UWA. Please see the main README.md in this repo for an introduction to using the Kaya server: https://github.com/cpflueger2016/Kaya-ListerLab-Tutorial/blob/main/README.md

## What is conda (and mamba) 

Installing software for computational biology can be a problem largely due to dependency hell (check out its wikipedia page, it is a serious enough thing that it has one). Dependency hell is when you need to install many other programs for your software of interest to work. What can make it wose is when you need to install two different versions of one package because two other programs each require a different version. 

Enter conda: conda is a package manager and an environment manager. As a package manager it can install your program of interest. As an environment manager, it can make multiple different vitual environments to each store different version of software to prevent conflicts of incompatpability between one and another. Think of a software environment as a bubble with all of the locations of relevant software loaded in and known by the machine. 

If you have some software that requires Python 2.7 but another that requires Python 3.6, they might not talk to each other well. So having one environment with just Python 2.7 and programs that use that (named py2, for example) and another with just Python 3.6 and related programs (named py3.6). Or you could seperate your environments by related projects (studying the PIN proteins of plants) or by a pipeline of analysing the same data type (like one for RNAseq analysis and another for DNA methylome analysis). 

`mamba` is just a version of `conda` that has been re-written to be faster. It is not installed on the Kaya server, unlike `conda` (see below), but you can install `mamba` via `conda` (sorry if this is getting Inception level of confusing). 

## Getting started with conda 

__Conda__ is already pre-installed on `Kaya`. In order to use `conda`, load the module

```bash
module load Anaconda3/2021.05
```

It's recommended and important to create a new `conda environment` with the prefix to point to the `group` data. There is more space on the `/group` volume and you can easily share the conda installation with your team members, so they don't have to re-install everything themselves.

An example of how to create a new conda environment would be:

```bash
conda create -p /group/<your_project_name>/conda_environments/bioinfo -c conda-forge mamba
```
Mamba is really useful for quicker installations in conda by replacing `conda` with `mamba`. For example, after mamba is installed, you can install `unicycler` with `mamba` by typing

```bash
mamba install -c bioconda unicycler
```


Once you have setup your conda environment, it's as easy as loading it by executing

```bash
conda activate /group/<your_project_name>/conda_environments/bioinfo
```

You should consider adding a default conda environment to your `~/.bashrc` so you can use your favourite programs right away (it is best practice to not install anything into the conda default enviroment `base` as this can cause unexpected behaviour that is hard to resolve).


