# fse21_paper270
Artifacts for paper #270 - Estimating Residual Risk in Greybox Fuzzing (Accepted at ESEC/FSE 2021)

## Authors
Marcel Böhme (Monash University), Danushka Liyanage (Monash University), Valentin Wüstholz (ConsenSys)

## Overview
No matter how long, there is always a non-zero probability to discover a software bug if we continue the fuzzing campaign a bit longer. Engineers need to know whether the residual risk is below the allowable threshold before deciding to stop the ongoing campaign. In fuzzing, residual risk is the probability to discover a bug from the next generated test input. In our probabilistic analysis, we suggest to use discovery probability; the probability to discover a new program behaviour as the upper bound for residual risk for fuzzing campaigns.

We show that the existing estimators of discovery probability are systematically and substantially under-estimate the true probability due to adaptive bias in greybox fuzzing. In this paper, we propose two classes of novel statistical estimators of discovery probability that account for adaptive bias in greybox fuzzing campaigns. 

## Generating results
We designed several simulation studies to support claims in the developed probabilistic analysis. The performance of the classical estimators (i.e. Laplace and Goog-Turing) and proposed novel estimators (i.e. Mean-local and a-Reset) of discovery probability were experimentally evaluated based on well-known statistical performance measures namely ‘bias’ and ‘variance’. For each simulation and experiment, we ensure maximum generalizability of the results by considering average behaviour of 20+ runs for each study.  

Through this repository, we make all the results that are presented in above paper openly accessible and reproducible. We would like researchers and practitioners to adopt the proposed estimators for deciding when to stop an ongoing greybox fuzzing campaign. 

## How to access results?
Within *'src'* directory, there are two separate R workbooks that allow to reproduce all the results presented in the paper. 

***Simulation.ipynb -*** This workbook consists of the simulation framework along with respective results obtained through greybox fuzzing simulations. 

***Empirical.ipynb -*** Contains the experimental results, evaluations of estimator performance, and all the plots/graphs presented in the experimental results section of the paper.

Generated plots/graphs are written to the directory named *'outputs'*.

## Reproduce results 
The public access allows anyone to edit the configuration and observe the results in both simulation and empirical evaluations. Such changes can be imposed and generate the same set of outputs (i.e. graphs) after cloning the workbooks to a local machine. A machine with regular specifications would be sufficient for the purpose. We outline a convenient and straightforward way to locally run the scripts using Anaconda Navigator.

* Install Anaconda Navigator community version using the instructions that are given [here](https://docs.anaconda.com/anaconda/navigator/). You need to have the latest version of R installed in your computer. R can be downloaded from [Cran](https://cran.r-project.org/bin/windows/base/) site.
* Open Anaconda Navigator and create a new R environment through ‘Environments’ tab.
* Return back to ‘Home’ and select the created R environment from the drop-down menu under ‘Applications on’.
* Launch JupyterLab and select the cloned repository from the local file system. 
* Now you can edit and run our workbooks.

Please note that you can use any other approach to edit and run the same Jupyter workbooks in your local computer. 

## Generating data for executing 'Empirical.ipynb'
We propose an experimental setup to empirically evaluate the estimator performance. we ran greybox fuzzing campaigns using LibFuzzer for longer time periods (close to one week) while establishing ground truth for discovery probability. The experiment generates all the required data for computing classical and novel estimators. The details on how to setup the experimental framework is extensively elaborated in the paper. We input the resulting csv data file to estimate and evaluate estimator performance in our ‘Empirical’ workbook. The csv data file for the conducted experiments resides in ‘data’ directory of this repository.

Please find the source code of our experimental setup under .......

## Cite our paper
The citation is currently unavailable. Will be updated once the paper will be published at ACM digital library. 

Temporary link:
https://esecfse2021.hotcrp.com/doc/esecfse2021-paper270.pdf
