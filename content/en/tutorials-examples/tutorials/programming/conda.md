---
title: "Conda environments"
linkTitle: "conda envs"
weight: 1
tags: ["python", "conda", "programming"]
author: Fernanda L. Ribeiro
aliases:
- /tutorials/programming/conda
description: > 
  A tutorial for setting up your conda environments on Neurodesk.
---


> _This tutorial was created by Fernanda L. Ribeiro._ 
>
> Email: fernanda.ribeiro@uq.edu.au
>
> Github: @felenitaribeiro
>
> Twitter: @NandaRibeiro93
>
<!-- Fill in your personal details above so that we can credit the tutorial to you. Feel free to add any additional contact details i.e. website, or remove those that are irrelevant -->

<!-- Following line adds a link to getting set up with Neurodesk -->
{{< params/neurodesktop/getting_set_up >}}
<!-- -->

This tutorial documents how to create conda environments on Neurodesk. 

## Conda/Mamba environment

The default conda environment is not persistent across sessions, so this means any packages you install in the standard environment will disappear after you restart the Jupyterlab instance. However, you can create your own conda environment, which will be stored in your homedirectory, by following the steps on this page. This method can also be used to install additional kernels, such as an R kernel.

1. In a Terminal window, type in:

![1_terminal](/static/tutorials-examples/tutorials/programming/conda/1_terminal.png '1_terminal')

For *Python*:
```bash
mamba create -n myenv ipykernel
#OR
conda create -n myenv ipykernel
```
or for *R*:
```bash
mamba create -n r_env r-irkernel
#OR
conda create -n r_env r-irkernel
```

**Important:** For Python environments, you have to set the ipykernel explicitly or a Python version (like "conda create -n myenv python=3.8"), since a kernel is required. Alternatively, in case it was forgotten, you can add a kernel with:

```bash
conda install ipykernel
```

2. To check the list of environments you have created, run the following:

```bash
mamba env list
#OR
conda env list
```

3. To activate your conda environment and install the required packages from a provided txt file, run:
For *Python*:
```bash
conda activate myenv
pip install -r requirements.txt
```
or for *R*:
```bash
conda activate r_env
pip install -r requirements.txt
```


4. Given the available environment, when you open a new Launcher tab, there will be a new Notebook option for launching a Jupyter Notebook with that environment active. 

![2_env](/static/tutorials-examples/tutorials/programming/conda/2_env.png '2_env')

Switching the environment on a Jupyter Notebook is also possible on the top right corner dropdown menu.

![3_notebook](/static/tutorials-examples/tutorials/programming/conda/3_notebook.png '3_notebook')
