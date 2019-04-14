
<a name = "top"></a>

# Contents

1. [Manage/Download/Delete a full anaconda environment](#part1)
	* [List Environment](#part1.list)
	* [Download new environment](#part1.download)
	* [Switch Environment](#part1.switch)
	* [Delete environment](#part1.delete)
2. [Create & share a new environment with pip](#part2)
	* [Create a skeleton python environment](#part2.newcreate)
	* [Check that you have pip installed](#part2.pip)
	* [Pip install with requirements.txt](#part2.install)
	* [Pip freeze to output requirements.txt](#part2.pipfreeze)
3. [Create & share a new environment with yaml](#part3)
	* [Generate yaml file from part2](#part3.yml)
	* [Create New conda environment from yaml file](#part3.clone)
	* [Tidying up](#part3.tidy)

Note that the integration of git with your device will be beyond the scope of this workshop. You may ignore `git:(master)` at the front of the working directory.

<a name="part1"></a>
## Part1

<a name="part1.list"></a>
#### List Environment
***

Inputs:

```
conda list env
```
Outputs:

```
➜  DSSGWS101 git:(master) ✗ conda env list
# conda environments:
#
base                  *  /Users/lowyixiang/miniconda3
```

<a name="part1.download"></a>
#### Download new (full) anaconda environment
***

Inputs: `conda create -n myenv python=x.x anaconda`

Example:

```
conda create -n py36 python=3.6 anaconda
```

There will be a prompt `Proceed ([y]/n)?` enter `y` and proceed.

Output:

```
...
...

# To activate this environment, use:
# > source activate py36
#
# To deactivate an active environment, use:
# > source deactivate
```

<a name="part1.switch"></a>
#### Switch Environment
***
Inputs:

```
source activate py36
```

You should observe that your CLI will change to:

```
(py36) ➜  DSSGWS101 git:(master) ✗

```

Upon switching environment, you can launch Jupyter Notebook which comes along with the full anaconda distribution.

Inputs:

```
jupyter notebook
```

Outputs:

A browser popup with address `http://localhost:8888/tree`. The working directory will be your current working directory in terminal. Enter `control+C` twice to exit back to terminal.

<a name="part1.delete"></a>
#### Delete Environment
***
Input:

```
conda remove --name py36 --all
```

When prompted with `Proceed ([y]/n)?` enter `y`.   

[return to top](#top)

<a name="part2"></a>
## Part 2

<a name ="part2.newcreate"></a>
### Create new skeleton environment
***

Inputs:

```
conda create -n py_pip python=3.6
```

Enter `y` upon prompt.

<a name ="part2.pip"></a>
### Check that you have pip installed
***

Inputs:

```
pip --version
```

#### To upgrade:

Inputs:    

```
pip install --upgrade pip
```
<a name ="part2.install"></a>


### Pip install with requirements.txt

***
Do take a look at how `requirements.txt` is defined.

Inputs: (With the requirements.txt in the current working directory)

```
conda activate py_pip
pip install --upgrade -r requirements.txt
```

If you run `python` in the terminal, you should now be able to `import django`. Type `quit()` in the console to exit back to the main screen.  

<a name ="part2.pipfreeze"></a>

### Pip freeze
***

to see your packages,      
Input:   

```
pip freeze
```

To export to a file, simply: `pip freeze > <filename>.txt`.   
Example:

```
pip freeze > requirements.txt
```

[return to top](#top)

<a name="part3"></a>
## Part 3

If you notice from [part2](#part2), you need to specify:

1. Name of environment
2. Python Version 

To overcome the above, we can use configure the environment with `yaml` file instead.

<a name="part3.yml"></a>
### Generate a yaml file 
***

Example:  `conda env export > <filename.yml>`.  
Inputs:

```
conda env export > environment.yml
```

Outputs a file `environment.yml`. Use your text editor or run `cat environment.yml` in your terminal. 

```
name: py_pip
channels:
  - defaults
dependencies:
  - ca-certificates=2019.1.23=0
  - certifi=2019.3.9=py36_0
  - libcxx=4.0.1=hcfea43d_1
  - libcxxabi=4.0.1=hcfea43d_1
  - libedit=3.1.20181209=hb402a30_0
  - libffi=3.2.1=h475c297_4
  - ncurses=6.1=h0a44026_1
  - openssl=1.1.1b=h1de35cc_1
  - pip=19.0.3=py36_0
  - python=3.6.8=haf84260_0
...
...
```

Go through the entire file to understand how the file is being structured.

<a name="#part3.clone"></a>
### Create New Conda Environment 

For more details on creating `conda environment manually`, check it out [here](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#create-env-file-manually).

***

Use your favourite text editor (or `nano` or `vim`) and edit:

```
name: py_pip
```

to

```
name: py_yml
```
In your terminal, run:

```
conda env create -f environment.yml
```

output:

```
#
# To activate this environment, use:
# > conda activate py_yml
#
# To deactivate an active environment, use:
# > conda deactivate
#
...
...
```
<a name="#part3.tidy"></a>
### Tidying up

***

Inputs:

```
conda env list
```

Outputs:

```
# conda environments:
#
base                  *  /Users/lowyixiang/miniconda3
py36                     /Users/lowyixiang/miniconda3/envs/py36
py_pip                   /Users/lowyixiang/miniconda3/envs/py_pip
py_yml                   /Users/lowyixiang/miniconda3/envs/py_yml
```

Delete the two environments by : (and enter `y` upon prompt)

```
conda remove --name py_pip --all
conda remove --name py_yml --all
rm environment.yml
```

[return to top](#top)
 