# Estimating Residual Risk in Greybox Fuzzing
For Artifact Evaluation at ESEC/FSE 2021

<a href="https://github.com/Adaptive-Bias/fse21_paper270/raw/main/esecfse2021-paper270.pdf"><img src="https://github.com/Adaptive-Bias/fse21_paper270/raw/main/esecfse2021-paper270.png" align="right" width="280"></a>

## Submission
* [Marcel Böhme](https://mboehme.github.io/) (Monash University)
* Danushka Liyanage (Monash University), and
* [Valentin Wüstholz](http://www.wuestholz.com/) (ConsenSys)
```bibtex
@inproceedings{residualrisk,
 author = {B{\"o}hme, Marcel and Liyanage, Danushka and W{\"u}stholz, Valentin}, 
 title = {Estimating Residual Risk in Greybox Fuzzing},
 booktitle = {Proceedings of the 15th Joint meeting of the European Software Engineering Conference and the ACM SIGSOFT Symposium on the Foundations of Software Engineering},
 series = {ESEC/FSE},
 year = {2021},
 numpages = {12},
}
```

## Overview
No matter how long, there is always a non-zero probability to discover a software bug if we continue the fuzzing campaign a bit longer. Engineers need to know whether the residual risk is below the allowable threshold before deciding to stop the ongoing campaign. In fuzzing, residual risk is the probability to discover a bug from the next generated test input. According to our probabilistic analysis, we suggest to use discovery probability (the probability to discover a new program behaviour) as an upper bound for residual risk for greybox fuzzing campaigns.

We show that existing estimators of discovery probability for blackbox fuzzing systematically and substantially under-estimate the true probability due to adaptive bias in greybox fuzzing. In this paper, we propose two classes of novel statistical estimators of discovery probability that account for adaptive bias in greybox fuzzing campaigns. 

## Validating our Claims
We designed and empirical and a simulation study to validate claims in our paper and the observations of our probabilistic model. The performance of the classical estimators (i.e. Laplace and Goog-Turing) and proposed novel estimators (i.e. Mean-local and a-Reset) of discovery probability were experimentally evaluated based on well-known statistical performance measures, namely ‘bias’ and ‘variance’. For each simulation and experiment, we address randomness as a threat to validity by considering average behaviour of 20+ runs for each study.  

Through this repository, we make all the results that are presented in above paper openly accessible and reproducible. We would like researchers and practitioners to adopt the proposed estimators for deciding when to stop an ongoing greybox fuzzing campaign. 

Given the time constraints of the artifact evaluation process, we do not provide instructions for reproducing the experimental results for LibFuzzer; it would take TODO CPU months to reproduce all results. Instead, we provide the raw data (`fse21_paper270/src/fuzzingdata.csv`) and an R workbook (`Empirical.ipynb`) for processing the data and generating plots and graphs. We provide a patch for LibFuzzer at TODO.

## Structure of this Repository
* Within *'src'* directory, you can find two separate R workbooks that allow to reproduce all the results presented in the paper. 
  * ***Simulation.ipynb -*** This workbook consists of the simulation framework along with respective results obtained through greybox fuzzing simulations. 
  * ***Empirical.ipynb -*** Contains the experimental results, evaluations of estimator performance, and all the plots/graphs presented in the experimental results section of the paper.
* Within the *'outputs'* directory, you can find the generated plots and graphs.

## Reproducing our Results 
We need to run the Jupyter notebooks. In the following, we specify the installation procedure for Windows. A similar installation procedure is recommended for other operating systems.

* Clone this repository: `git clone https://github.com/Adaptive-Bias/fse21_paper270`
* Install [R](https://cran.r-project.org/bin/windows/base/) and [Anaconda Navigator](https://docs.anaconda.com/anaconda/navigator/) community version.
* Open Anaconda Navigator and create a new R environment through ‘Environments’ tab.
* Return back to ‘Home’ and select the created R environment from the drop-down menu under ‘Applications on’.
* Launch Jupyter and navigate to the the cloned repository. 
* Edit and run our workbooks in the folder in the folder `fse21_paper270/src`.
* Find the data for `Empirical.ipynb` in `fse21_paper270/src/fuzzingdata.csv`.

Please refer to **INSTALL.md** and **REQUIREMENTS.md** for more details on how to run workbooks locally.
