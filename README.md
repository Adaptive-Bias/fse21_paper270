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

## Structure of this Repository
* Within *workbooks* directory, you can find two separate R workbooks that allow to reproduce all the results presented in the paper. 
  * ***Simulation.ipynb -*** This workbook consists of the simulation framework along with respective results obtained through greybox fuzzing simulations. 
  * ***Empirical.ipynb -*** Contains the experimental results, evaluations of estimator performance, and all the plots/graphs presented in the experimental results section of the paper.
* Within the *outputs* directory, you can find the generated plots and graphs.
* Within the *data* directory, you can find the data from which the plots and graphs are generated.

## Reproducing our Simulation and Empirical Analysis 
We need to run the Jupyter notebooks. In the following, we specify the installation procedure for Windows. A similar installation procedure is recommended for other operating systems. For more details, please see refer to **INSTALL.md** and **REQUIREMENTS.md**.

* Clone this repository: `git clone https://github.com/Adaptive-Bias/fse21_paper270`
* Install [R](https://cran.r-project.org/bin/windows/base/) and [Anaconda Navigator](https://docs.anaconda.com/anaconda/navigator/) community version.
* Open Anaconda Navigator and create a new R environment through ‘Environments’ tab.
* Return back to ‘Home’ and select the created R environment from the drop-down menu under ‘Applications on’.
* Launch Jupyter and navigate to the the cloned repository. 
* Edit and run our workbooks in the folder in the folder `fse21_paper270/workbooks`.
* Find the data for `Empirical.ipynb` in `fse21_paper270/data/fuzzingdata.csv`.
* If you have problems running the Jupyter notebooks, you can refer to our copies on Kaggle (see below).

## Generating Fuzzing Data for Empirical Analysis
We perform our experiments in **Libfuzzer**. We chose six subjects from the fuzzing benchmarking platform, Fuzzbench. The resulting csv data file from this experiment is used as the input data file for generating our emprirical results through ***Empirical.ipynb***. Refer *data* directory for accessing the generated  experimental data. We provide the *diff* for LibFuzzer along with the execution instructions for reproducing our experimental data.

The diff can be found at https://raw.githubusercontent.com/Adaptive-Bias/fse21_paper270/main/data/fuzzbench.diff

Assume that we choose the subject ```freetype2-2017``` and the trial number ```1```. Successful execution of following commands will produce the csv named ```freetype2-2017.1.csv```. Make sure that the experiment has to be continued for a longer period (until fuzzer generates more than *10^9* test inputs) with more trials to generate same results for the selected set of subjects.

```
git clone https://github.com/google/fuzzbench
cd fuzzbench
git checkout 7b92df520aa9794fc483441e90db1c725859e5a3
git submodule update --init
git apply --ignore-whitespace fuzzbench.diff # Adds the diff to the code
sudo apt-get install build-essential
sudo apt-get install python3-dev python3-venv
make install-dependencies

source .venv/bin/activate
sudo make run-entropic-freetype2-2017 > freetype2-2017.1.csv
```
To see the progress of the campaign, run the below command in a seperate terminal.

```
tail -f freetype2-2017.1.csv
```

## Kaggle Notebooks

We have also published both of our workbooks namely *Simulation* and *Empirical* as Kaggle notebooks. The scripts are publically accessible via below links:

- https://www.kaggle.com/adaptivebias/simulation
- https://www.kaggle.com/adaptivebias/empirical
