# There are 3 types of ways to create a virtual environment in python

Source: [https://medium.com/@krishnaregmi/pipenv-vs-virtualenv-vs-conda-environment-3dde3f6869ed]

# WARNING
> **WARNING**: Please do not intermingle the use of >1 package manager - CHOOSE ONE TYPE OF PACKAGE MANAGER - I AM USING REGULAR PIP. This is because the use of different package managers affects the PATH where default installations go to. Hence causing ambiguity or packages that does not work properly. If different installations lead to different installed location/ path, then packages/ dependencies can become segregated, as different package mangers assumes different places where you want your installation to go. (I have personally had the trouble uninstalling packages, deleting directories and package managers for an entire day, when I attempted to install tensorflow, which i failed, where I later discovered a "system-path-installation-confusion" in my system caused by my early installations from different package managers and software: homebrew, conda, pip, python installations.)

### What is a virtual environment vs Jupyter kernel?
(Not verified)
(https://medium.com/@SMNWYP0710/conda-env-kernel-and-jupyter-notebook-in-gcp-52d51d09f1f9)
(https://arshren.medium.com/how-to-setup-conda-environments-and-add-kernels-for-jupyter-notebook-f2ebf968a409)
- **Jupyter Kernel** (session host, like a separate computer): A runtime environment that provides programming language support for the Jupyter Notebook application - so that we can run "cells" in jupyter notebook which is just an interface for ipykernel. When a notebook is opened in edit mode, only one interactive session connects to a Jupyter Kernel for the notebook language. This kernel runs code that you send (from the cell into the ipykernel), and returns the computational results.
- **Virtual environment** (package tracker): An isolated environment which isolates installed 1) Python interpreter, 2) libraries, 3) scripts from other virtual environment and the system "base" (default).

> A **KERNEL (ipython kernel) MUST EXIST before a virtual environment (BUT by default, there is always a "base" kernel, which is the system's root session), which can be used to host.** (But notice one python kernel might not be enough, as we introduce another dependencies for other programming languages - R, ...)
	- A virtual environment must be linked to 1 Kernel to designate the host used to run the virtual environment.

- Similarities: Both provides isolation.
- Differences: 
- Kernel isolates jupyter runs as an isolated session, while a virtual environment isolates things like 1) interpreters, 2) libraries, 3) scripts within the kernel/ session?
- Advantage of having a kernel:
	- Keep their kernel isolated, as they might have different kernels for differen tasks/ workflows.
- Advantages of having a virtual environment:
- [Reddit Explaination](https://www.reddit.com/r/IPython/comments/ni9n0w/help_venv_vs_kernel/)

----------------------
# Virtualenv
1) virtualenv
-----
## (Install, done once)
>$ pip install virtualenv 

## (Create a virtual environment)
> $ virtualenv venv 	
>> At this point, you will see a `venv` dir generated. It can be renamed.	

## (activate virtual environment in your terminal)
> $ venv/Scirpts/activate 

**Good practices**
> $ pip freeze > requirements.txt `This allows a record of all dependencies in venv to be stored`
> $ pip install -f requirements.txt `Creating a new virtual environment form requirements.txt file`

> Notice we use pip and virtualenv together, what if we can merge them together? Enter pipenv

----------------------
# Pipenv
2) pipenv (USED because its shorter and safer)
------	
## Prereq
- Install ipykernel: `pip install ipykernel`
- Install pipenv: $ `pip install pipenv`

## 0. (Create new KERNEL in jupyter notebook)
> $ python -m ipykernel install --user --name=my-virtualenv-name

## 1. (Activate a virtual environment OR Create virtual environment IF it does not exist AND activate it) 
> $ pipenv install 
- At this point, you will see a `pipfile` file generated.


## 2. (Activate virtual environment)
> $ `pipenv shell`
> Notice how much shorter code is in order to create + activate a virtual environment
- Deactivate virtual environment
> `exit`

## 3. Install dependencies/ packages into pipenv
- Note: This is not the same as `pip install {package_name}` which install dependencies into the base
> `pipenv install {package_name}`
> `pipenv install {package_name==version_id}`

- Uninstall dependencies/ packages in pipenv
> `pipenv uninstall {package_name}`

## Install dependencies/ packages from requirements.txt file 
- `requirements.txt`: A generic textfile named- "requirements", which lists all the dependencies in a straightforward way, which can be read by any virtual environment handler, and install packages accordingly.
> `pipenv install -r requirements.txt`

## Exporting dependencies to 'requirements.txt' file
- Exporting all dependencies only list in the pipfile.lock 
> `pipenv lock --requirements > requirements.txt`
	- generates a `requirements.txt` file based on the dependencies specified in the `Pipfile.lock` file. It includes all the dependencies, their versions, and any transitive dependencies, ensuring that you get an exact replica of the virtual environment. This command is specific to `pipenv` and requires that you have a `Pipfile.lock` file.

- Exporting all dependencies only list in the pipfile.lock (NOT a pipenv command)
> `pip freeze > requirements.txt`
	- generates a `requirements.txt` file based on the packages installed in the active environment. It includes all the packages, their versions, and any transitive dependencies. However, it does not distinguish between direct and transitive dependencies and may include packages that are not strictly required. This command is a general `pip` command and can be used with any Python environment. 

## Updating dependencies
> `pipenv update`
- used to update packages in a Pipenv environment. It updates packages specified in the Pipfile.lock to the latest compatible version according to the version constraints specified in the Pipfile. If no version constraints are specified, it will update packages to their latest versions.
- This ensures that all developers and servers are using the exact same dependencies and versions, and helps avoid conflicts and incompatibilities.

## Check vulnerability in dependencies
> `pipenv check`
- `pipenv check` command is used to check for security vulnerabilities in the project's dependencies. It runs a security check against the installed packages using the PyUP.io service, which checks the packages against a database of known vulnerabilities.
- By running `pipenv check`, you can identify potential security issues in the project's dependencies, which can help you to proactively address any vulnerabilities and keep your project secure. This is especially important in production environments where security is critical.

## Check packages/ dependency graph 
> `pipenv graph`

## Check path to where the virtual environment is stored
> `pipenv --venv`
- We can delete the pipenv virtual environment directly to remove the virtual environment, instead of using pipenv uninstall as a more manual method.


- `Pipfile` specifies the dependencies that should be used, and the `Pipfile.lock` specifies the exact versions of those dependencies that are currently installed and should be used.

## Check path to where a package is stored
> `pip show {package_name}`

----------------------
# Conda
- Conda is a package, dependency, and virtual environment (environment) MANAGER. For languages: Python, R, Ruby, Lua, Scala, Java, JavaScript, C/ C++, Fotran, and more...
3) conda (USED because nobody wants to install xxx this will work as long as you have python, because anaconda (conda) is a distribution of python, and it produces a yml file, which is more consistent)

Resources:
- https://www.earthdatascience.org/courses/intro-to-earth-data-science/python-code-fundamentals/use-python-packages/use-conda-environments-and-install-packages/
- http://echrislynch.com/2019/02/01/adding-an-environment-to-jupyter-notebooks/

----------------------

> Contents are numbered suggesting priority and most likely used, and separating the superfluous.

## Prereq
- Install ipykernel: `conda install -c anaconda ipykernel`

## 0. (Create and install new kernel into system)
> $`ipython kernel install --user --name={name_of_new_kernel}`
- `name_of_kernel` that is created can be anything. But recommended to be the same as the environment, so reduce ambiguities.

## 1. (Create a new virtual environment)
> $`conda create -n {name_of_new_virtual_env} python={version_no}`
> $`conda create -n {name_of_new_virtual_env}`

- Common names for virtual environments: If you are storing your environment inside the project folder some common names are `env`, `venv`, `.env`, `.venv`, but besides that, I don't think there are any common conventions.

## 2. (Activate virtual environment)
> $`conda activate {name_of_new_virtual_env}`
- After "activating" your chosen virtual environment our terminal will connect to that virtual environment, hence allowing us to see kernel name at the terminal prompt. E.g., (`(virtual_env_name) C:\Users\Jack>`)
- Deactivate virtual environment
	- $`conda deactivate`

## 3. (INSTALL new packages into virtual environment without YAML files)
> $`pip install {new_package}`
> $`conda install {new_package}`
> $`conda install {new_package}={version}`
> $`conda install -name {name_of_virtual_env} {name_of_new_package}`
> OR
> $`conda install -c conda-forge {name_of_new_package}`
	- conda-forge (-c means --channel) , using **conda-forge** channel when installing the package. It is bad practice to mix channels. and **conda-forge** currently has the most well maintained and broad range of available libraries.

## (Cloning an existing virtual environment to a new virtual environment)
> $`conda create -n {name_of_virtual_env} --clone {cloned_virtual_env}`

## (List ALL virtual environment in kernel)
> $`conda env list`

## (Remove virtual environment from kernel)
> $`conda env remove -n {virtual_env_name}`

## 4. (List ALL installed packages in virtual environment)
> $`conda list`

## (CREATING YAML)
## (Creating and tracking your virtual environment packages WITH YAML files)
> $`conda env create -f environment.yml`

- **Good practices**
	`Save all info (package dependencies installed) necessary to recreate the environment in a file by calling`:

## (IMPORT & EXPORT YAML)
## (Importing dependecies/ list of packages from a YAML file to the current environment)

> $`conda env update -f {yaml_file_containing_dependencies.yml}`

## 5. (Exporting dependencies/ list of packages in the virtual environment into a YAML file)
>$ `conda env export > environment.yml`

- Notice it is more migration friendly, as it stores all the dependencies properly in a yml file (yml file is commonly used for configuration files and in applicaitons where data is being stored or transmitted)

## 6. (List all created virtual environments with conda)
> $`conda env list`

## (Uninstalling virtual environment from jupyter)
> $`jupyter kernelspec uninstall envname`

## (Install pip) (if conda does not have wanted packages): 
> $`conda install pip`

----------------------

# Generic commands

Kernel
- Kernel commands are the same for all virtual environments we choose to use above.
- Install ipykernel: $`pip install ipykernel`


## List all installed kernels in jupyter notebook
$ `jupyter kernelspec list`

## Creating a new kernel 
- (same step for all virtual environment above)
`(your-venv)$ ipython kernel install --name "local-venv" --user`
- or
$ `python -m ipykernel install --name={kernel_name}`

## Removing kernel
$`jupyter kernelspec remove {kernel_name}`

## Activate virtual environment
$ `source name-of-venv/bin/activate`

## Changing the name of the kernel
1. Use $`jupyter kernelspec list` to see the folder the kernel is located in.
2. cd to the folder, and open file named `kernel.json`
3. Edit the option/ key: `"display_name"`

Virtual environments
- COMMADS are specific to the virtual environments we use. Hence view each.