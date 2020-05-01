# Interactive Work Environment

## Weblab at CAU Kiel

For the module "PherWiss: Angewandtes Programmieren" we will use a web-based interactive computing environment to do the exercises.
The URL of the platform is https://weblab.uni-kiel.de and it is based on [Jupyter Lab](https://jupyterlab.readthedocs.io/en/stable/).
The system is reachable from everywhere in the world, so no VPN connection to the universities network is necessary.
I recommend to take a look at the [Jupyter Lab User Guide](https://jupyterlab.readthedocs.io/en/stable/user/interface.html) to make yourself comfortable with the user interface.

Access to the system is restricted to registered users.
The user accounts are created and assigned during the first exercise class.
The password for the accounts is set by you and it is the password that you enter when you first login.
Please remember your password carefully, since password reset is not easily possible.

Please note that your account and all of your data will be deleted after the end of the second examination period of the summer term.
Make a backup of all your data on your local machine by [downloading](https://jupyterlab.readthedocs.io/en/stable/user/files.html#uploading-and-downloading) all relevant files.

## Python on your machine

To install a similar environment on your own computer, I recommend to install the [Anaconda](https://www.anaconda.com/) or [Miniconda](https://docs.conda.io/en/latest/miniconda.html) distribution.
Anaconda is a Python distribution for scientific data analysis.
It comes with most of the commonly used packages already installed.

Further packages can be installed from the internet using the [conda package manager](https://docs.conda.io/projects/conda/en/latest/).
For example, to install Jupyter Lab, you can run
```bash
conda install jupyterlab
```

When you gain more experience with managing packages, you should make yourself comfortable with the idea of [virtual environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html).
These allow to specify multiple environments which may differ in terms of installed packages or package versions.
By installing the package [nb_conda_kernels](https://github.com/Anaconda-Platform/nb_conda_kernels) into the environment in which Jupyter Lab is installed, all virtual environments which have a Jupyter kernel package (e.g. [ipykernel](https://github.com/ipython/ipykernel)) installed are available to run a Jupyter notebook.
