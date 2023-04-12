# There are 3 types of ways to create a virtual environment in python

Source: [https://medium.com/@krishnaregmi/pipenv-vs-virtualenv-vs-conda-environment-3dde3f6869ed]

What is a virtual environment vs Jupyter kernel?
- **Jupyter Kernel** (session): A runtime environment that provides programming language support for the Jupyter Notebook application. When a notebook is opened in edit mode, only one interactive session connects to a Jupyter Kernel for the notebook language. This kernel runs code that you send, and returns the computational results.
- **Virtual environment** (package tracker): An isolated environment which isolates installed 1) Python interpreter, 2) libraries, 3) scripts from other virtual environment and the system "base" (default).
- Similarities: Both provides isolation.
- Differences: 
- Kernel isolates jupyter runs as an isolated session, while a virtual environment isolates things like 1) interpreters, 2) libraries, 3) scripts within the kernel/ session?
- Kernel stores a subset of dependencies from the Base/ System root, virtual environment points to those dependencies? ( Virtual env $\subseteq$ Kernel $\subseteq$ Base )?
	- Base is the gate to the neighborhood, Kernel is like the gate to the house, while virtual environment are doors in a house?
- Advantage of having a kernel:
	- Keep their kernel isolated, as they might have different kernels for differen tasks/ workflows.
- Advantages of having a virtual environment:

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

## (Activate a virtual environment OR Create virtual environment IF it does not exist AND activate it) 
> $ pipenv install 
	>> At this point, you will see a `pipfile` file generated.

## Install dependencies/ packages into pipenv
- Note: This is not the same as `pip install {package_name}` which install dependencies into the base
> `pipenv install {package_name}`
> `pipenv install {package_name==version_id}`

## Install dependencies/ packages from requirements.txt file 
- `requirements.txt`: A generic textfile named- "requirements", which lists all the dependencies in a straightforward way, which can be read by any virtual environment handler, and install packages accordingly.
> `pipenv install -r requirements.txt`

## (Activate virtual environment)
> $ pipenv shell
> Notice how much shorter code is in order to create + activate a virtual environment

## (Activate kernel in jupyter notebook)
> $ python -m ipykernel install --user --name=my-virtualenv-name


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

## (Create and install new kernel into system)
> $`ipython kernel install --user --name={name_of_new_kernel}`
- `name_of_kernel` that is created can be anything. But recommended to be the same as the environment, so reduce ambiguities.

## 1. (Create a new virtual environment)
> $`conda create -n {name_of_new_virtual_env} python={version_no}`
> $`conda create -n {name_of_new_virtual_env}`

## 2. (Activate virtual environment)
> $`conda activate {name_of_new_virtual_env}`

## 3. (INSTALL new packages into virtual environment without YAML files)
> $`conda install -name {name_of_virtual_env} {name_of_new_package}`
> OR
> $`conda install -c conda-forge {name_of_new_package}`
	- conda-forge (-c means --channel) , using **conda-forge** channel when installing the package. It is bad practice to mix channels. and **conda-forge** currently has the most well maintained and broad range of available libraries.

### (Installing stuff not into virtual environment)
> $`conda install {name_of_new_package}`

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
>$ conda env export > environment.yml

- Notice it is more migration friendly, as it stores all the dependencies properly in a yml file (yml file is commonly used for configuration files and in applicaitons where data is being stored or transmitted)

## 6. (List all created virtual environments with conda)
> $`conda env list`

## (Uninstalling virtual environment from jupyter)
> $`jupyter kernelspec uninstall envname`

## (Install pip) (if conda does not have wanted packages): 
> $`conda install pip`

----------------------

# Generic commands

## Installing NEW packages in all three methods
$ pip install <package>

## List all installed kernels in jupyter notebook
$ jupyter kernelspec list


## Add virtual environment as a jupyter kernel
$ ipython kernel install --name "name-of-venv" --user

## Activate virtual environment
$ source name-of-venv/bin/activate