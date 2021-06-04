# Installation

We provide a simple and convenient way to execute the workbooks with extension .ipynb in *'src'* directory.

## Prerequisites

The following software has to be installed in your local machine (work for any operating system including Windows, Mac, or Linux)
  - Latest version of the statistical package ***R***. If R is not available in your loacl machine, download R from https://cran.r-project.org/bin/windows/base/ and follow the provided instructions in [this link](https://www.datacamp.com/community/tutorials/installing-R-windows-mac-ubuntu) based on your operating system to install R. 
  - The individual edition of ***Anaconda Navigator***. The installation package and intructions can be found at https://docs.anaconda.com/anaconda/navigator/

## Clone and Launch JupyterLab
  - Clone this repository to the local machine. (https://github.com/Adaptive-Bias/fse21_paper270.git) 

We intend to launch the Jupyter workbooks using the JupyterLab through Anaconda Navigator. Before launching, we have to create a new R environment within Anaconda Navigator as our language of interest is R.
Below are the steps to create a new R environment through GUI.

  - Open Anaconda Navigator.
  - Enter to *'Environments'* tab from the menu on left hand side.
  - Create a new R environment with desired name by clicking the button *'Create'*. (Make sure you uncheck python from the dialog box) 
  - Return back to *'Home'*. Select the created R environment from the drop down menu under *'Applications on'*.

Now you are all set for launching ***JupyterLab***.

  - Click on JupyterLab **Launch** button from home window of Anaconda Navigator.

JupyterLab opens on the browser.

## Open and Run Our Workbooks

The local file system is appearing in the left side bar in opened JupyterLab window. (If not, **view -> Show Left Sidebar** from menubar)

  - Reach to the cloned repository from the file system and open the required .ipynb workbook (Simulation.ipynb or Empirical.ipynb) on JupyterLab.
  - Before, running the workbooks, make sure you have installed all the required R libraries that are mentioned in ***REQUIREMENTS.md***. You may use the following line of code to install a required package.
    ```
    install.packages(<package_name>,dependencies=TRUE)
    example: if you need to install the package, "ggplot2"
    install.packages("ggplot2",dependencies=TRUE)
    
    ```
    
  - If you need to install a specific version of an R package, you may use the below functions to achieve that. The specific R package versions are also stated in ***REQUIREMENTS.md***.
  ```
  install.packages("remotes")
  library(remotes)

  install_version("tidyverse", version = "1.2.1", repos = "http://cran.us.r-project.org")
  install_version("tidyr", version = "1.1.3", repos = "http://cran.us.r-project.org")
  install_version("dplyr", version = "1.0.6", repos = "http://cran.us.r-project.org")
  install_version("ggplot2", version = "3.1.1", repos = "http://cran.us.r-project.org")
  install_version("gridExtra", version = "2.3", repos = "http://cran.us.r-project.org")
  install_version("scales", version = "1.0.0", repos = "http://cran.us.r-project.org")
  install_version("grid", version = "3.6.1", repos = "http://cran.us.r-project.org")
  install_version("RColorBrewer", version = "1.1-2", repos = "http://cran.us.r-project.org")
  ```

Now, you can edit and run the workbooks in this repository. Instruction on using JupyterLab can be found [here](https://jupyter.org/).

## Other Methods

We need to stress that this is not the only way to edit and run the Jupyter workbooks. Yet, we found this method very convenient to setup and execute. You are free to use any other method that serves the same purpose.
