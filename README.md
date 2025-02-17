# Python Programming for Earth Observation Data Tutorial

This tutorial aims to provide a comprehensive introduction to programming in Python for
Earth Observation (EO) data analysis. We will utilize an interactive computing
environment based on the Jupyter ecosystem and leverage software packages endorsed by the
Pangeo community. To facilitate collaboration and version control, we will communicate
the tutorial content using git version control and provide instructions on how to use the
GitHub client. The software environment is extensive, but can be used for
most (big) environmental data analysis projects. The installation instructions
provided here are based
on the [CoastalCodeBook](https://github.com/floriscalkoen/coastalcodebook), a pilot in
the Coastal Systems 2023 MSc course at Delft Technical University. The following subsections will guide you through the three configuration
steps required to get started. 

### 1. Accessing the Code Repository with Git

If you are not familiar with using Git, please have a look at this short but excellent
[introduction](https://earth-env-data-science.github.io/lectures/environment/intro_to_git.html)
first.

1) Please refer to the [GitHub Client documentation](https://desktop.github.com/) to
   install the GitHub client, or see [these
   instructions](https://github.com/git-guides/install-git) to install git using the
   command line.

2) Clone this repository to your local computer using either of the following options:
   
   1. **GitHub client**: Browse to the
   [webpage](https://github.com/Deltares/py-sense.git), click on the green "Code"
   button and select "Open with GitHub Desktop", or paste the URL into the GitHub client.

   2. **Bash shell**: If you have a bash terminal available that has
      [git](https://docs.github.com/en/get-started/getting-started-with-git) installed, you
   can simply run: ` git clone https://github.com/Deltares/py-sense.git`. 

By following these steps, the files that are hosted on GitHub will be "pulled" to your machine. However, we cannot do anything with the files yet, as we still need to install the software that can understand the code. Continue with the next section to install a package manager.

### 2. Mamba package manager

If you're not familiar with managing Python environments, please have a look at this
[introduction](https://earth-env-data-science.github.io/lectures/environment/python_environments.html?highlight=conda)
first. The bottom line is that it is good practice to manage your software environments
to avoid dependency conflicts. For the tutorial notebooks, we recommend to use the
lightweight package manager `mambaforge`. The instructions to install this package
manager can be found in [their
documentation](https://mamba.readthedocs.io/en/latest/installation.html), in which they
refer to the [Conda Forge GitHub](https://github.com/conda-forge/miniforge#mambaforge)
page to download the software. 

#### Windows

**Known issues**: Some users have their firewalls configured in such way that the
mambaforge installation is blocked. If you have trouble installing mambaforge, please make
sure to temporarily disable your firewall. 

1. Download the mambaforge executable file for Windows from [Miniforge GitHub
page](https://github.com/conda-forge/miniforge#mambaforge). On that page there are also
binaries for Mac and Linux; and for `conda` package managers, so make sure you download
the `mambaforge` executable file for Windows. Install the executable by clicking on it;
you can stay with the default settings by just clicking next through the installation
client. 
2. Now that mambaforge is installed, you can open a `Miniforge Prompt`. You can open this
   shell by opening the start window and search for "Miniforge". 

#### Unix like - Mac and Linux
1. We recommend to install Mambaforge on Linux and Mac using a terminal. On Mac, you can
   open a terminal by searching for "terminal" or "iterm". On Linux the hotkey to open a
   terminal is "cntrl + shift + t". The commands to
   install the package manager are copied from their documentation and can be run by
   copying the commands below over to your terminal and pressing enter:  
   ```bash
   curl -L -O "https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-$(uname)-$(uname -m).sh"
   bash Mambaforge-$(uname)-$(uname -m).sh

   ```
2. Accept the user agreements, and allow the installation script to edit your profile
   file. The profile file (`~/.bashrc` on Linux or possibly `~/.zshrc` on Mac) is the
   first script which is being executed when you open a new terminal. The installation
   script will add a few lines to that file to make the `mamba` command available every
   time open a new terminal. 
3. Close the terminal. 

### 3. Software environments 
To run the tutorial notebooks we need several packages. To avoid dependency conflicts it
is good practice to seperate your environments; that was the reason for installing a
package manager. Now that we have our package manager we will create the software
environments. We will create one environment that runs the JupyterLab IDE, including
several extensions; and another one that contains the packages that we need for the
tutorials. 

1. Now that mambaforge is available on your machine, open a terminal. On Windows you
   should open the Miniforge prompt, which you can find by searching for it in the Start
   window. On Mac you can open a terminal by searching for "terminal" or "iterm". For
   Linux it's "cntrl + shift + t". 
2. You can check if mamba was installed by running the following command in the terminal: 
   ```bash 
   mamba --version
   ```` 
   It should output something like: 

   ```console
   ~ base ❯ mamba --version
   mamba 1.1.0
   conda 22.9.0
   ```
3. Now that mambaforge is installed, navigate in the terminal to the directory
   where you cloned the GitHub py-sense repository. You can navigate the terminal
   using `cd`, which stands for "change directory". 
   - **Windows**: if you are on Windows and you installed the GitHub client using their default settings you can
   simply run `cd %userprofile%\Documents\GitHub\py-sense`. 
   - **Linux/Mac**: change to the directory where you cloned the GitHub repository. This
     will be something like `cd ~/path/to/github/repository`. 
4. The py-sense root directory contains two yaml files, that describe the software
   dependencies. The first one, [environment-jupyterlab.yml](environment-jupyterlab.yml)
   contains some packages and several extensions to build an interactive Jupyter
   environment. The other one, [environment.yml](environment.yml), is a
   specification for required software that we will use in the tutorial notebooks. First
   create a Jupyterlab environment by running: 
   
   ```bash
   mamba env create -f environment-jupyterlab.yml
   ```

   And then create the coastal environment by running: 
   ``` 
   mamba env create -f environment.yml
   ``` 
   Depending on whether this is the first time to install this kind of software on your
   machine, this might take a few minutes to complete. If you want to give other names to
   the environments you can do so by adding a `-n` or `--name` flag, i.e., 
   ```bash
   mamba env create -n testenv -f environment-jupyterlab.yml
   ``` 

## Running the tutorial notebooks 
Now that you have access to the code (cloning this Github repository), installed a
package manager and created your environments we can start running the notebooks in
Jupyterlab. If you are new to JupyterLab we encourage you to have a look at [this
introduction](https://earth-env-data-science.github.io/lectures/environment/intro_to_jupyterlab.html). 

1. Open a terminal or Miniforge prompt. 
2. Change to the directory where you cloned the repository `cd </path/to/local/repo>`.
   Note, on Windows you should use backslashes. 
3. Activate your Jupyterlab environment by running: 
   ```bash
   mamba activate lab
   ```
4. Open Jupyterlab by running the following command: 
   ```bash
   jupyter lab 
   ```
   This will open a Jupyterlab client in your browser. 
5. In the jupyterlab you browse to the `notebooks` directory and open
      one of the notebooks, for instance,
      [01_data_access.ipynb](notebooks/01_data_access.ipynb).
6. Once the notebook is open you can activate the `pysense` environment in the
      upper-right corner; change `Python 3 (ipykernel)` to `Python [conda env:pysense]`.  
7. Now you can run the cells and do some interactive coastal analysis!
