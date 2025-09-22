# Reprolab demo
> [!WARNING]
> This proof of concept only works on files in the home directory and requires you to set a gitignore to prevent all files in your virtual lab from being committed. Do not use this for actual virtual lab development.

## Getting started

1. Open the file browser and navigate to your home directory

   ![navigate-to-home.png](img/navigate-to-home.png)

2. Create a new Python notebook
> [!WARNING]
> Create the notebook in the home directory. This proof of concept only works if the Reprolab code is run from a notebook in the home directory.

> [!WARNING]
> Only Python is currently supported.

   ![create-notebook.png](img/create-notebook.png)

3. Open the Reprolab panel

   ![open-reprolab.png](img/open-reprolab.png)

4. Click on “Add Demo Cell”

   ![add-demo-cell.png](img/add-demo-cell.png)

## Reproducibility checklist

You can interact with the reproducibility checklist. Results are saved to `~/reprolab_data/reproducibility_checklist.json`

## Environment management

1. Click on “Create Environment”. This step can take while. This creates a new environment in `~/my_venv`.

   ![create-environment.png](img/create-environment.png)

   At this point, you can restart your virtual lab instance to use the newly-created environment as a notebook kernel. To do so, click on “File > Logout” and start the virtual lab again. You can then select the environment from the list of available kernels.

2. Click on “Freeze Dependencies”. This creates a list of the dependencies installed in the current environment in `~/requirements.txt`. This file can later be used to install the dependencies on a different machine.

## Experiment managment

To use the experiment management feature, we first need to create a git repository.

1. Open the terminal

   ![open-terminal.png](img/open-terminal.png)

2. Type the following commands:

   ```shell
   git init
   git config --global user.email 'you@example.com'
   git config --global user.name 'You'
   git config --global --add safe.directory /home/jovyan
   echo -e '* \n!requirements.txt \n!reprolab_data/reproducibility_checklist.json \n!*.ipynb' > .gitignore
   ```
   The last command "`echo ...`" creates a gitignore file ignoring everything, except: `requirements.txt`, `reprolab_data/reproducibility_checklist.json` and any `.ipynb` files in the home directory.

> [!WARNING]
> Incorrectly setting up your gitignore can lead to committing secrets. Make sure you only include files in git tracking that don't contain secrets.

3. Go back to the notebook and click on “Create Experiment”. This commits your changes and creates a tag.
