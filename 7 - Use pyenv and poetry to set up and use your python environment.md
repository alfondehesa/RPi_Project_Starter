# 7- Use pyenv to set up your Python environment

## Table of contents

- [ ] [Summary](7%20-%20Use%20pyenv%20and%20poetry%20to%20set%20up%20and%20use%20your%20python%20environment.md#summary)
- [ ] [Install `pyenv` and `poetry`](7%20-%20Use%20pyenv%20and%20poetry%20to%20set%20up%20and%20use%20your%20python%20environment.md#install-pyenv-and-poetry)
- [ ] [Start a project with `pyenv` and `poetry`](7%20-%20Use%20pyenv%20and%20poetry%20to%20set%20up%20and%20use%20your%20python%20environment.md#start-a-project-with-pyenv-and-poetry)
- [ ] [Open a project with `pyenv` and `poetry`](7%20-%20Use%20pyenv%20and%20poetry%20to%20set%20up%20and%20use%20your%20python%20environment.md#open-a-project-with-pyenv-and-poetry)
- [ ] [Manage dependencies](7%20-%20Use%20pyenv%20and%20poetry%20to%20set%20up%20and%20use%20your%20python%20environment.md#manage-dependencies)
- [ ] [Next Steps](7%20-%20Use%20pyenv%20and%20poetry%20to%20set%20up%20and%20use%20your%20python%20environment.md#next-steps)

## Summary

- **Virtual environments** are **independent installations of Python** and packages.
- They are used for **managing dependencies that might be specific to your project**.
- For instance, your project might need a **specific version of Python** or a **specific Python package**. Virtual environments allow you to have a **contained instance of the right version of Python with the right version packages**, to make running your project easier.

### Pyenv

- **Pyenv is a virtual environment tool**, that focuses specifically on **managing different versions of Python** in your system.
- Pyenv is useful to run projects that have been designed around a **specific version of Python**, and might not work on other versions.
- In such a case, you would use `pyenv` to **install and use a specific version of Python**.

### Poetry

- **Poetry** is another virtual environment tool that focuses more on **package managing**.
- If only certain version packages work on your project (i.e. a specific version of `numpy` or a specific version of `Pandas`, etc.), it's a great tool that can be used to **define specific project dependencies**.
- By installing Poetry in your different machines, you will be able to **very easily install every single package required** for the project by running a simple `poetry install` command in the project directory.
- If you have the right version of Python installed in your machine (with `pyenv`, for example), then running `poetry shell` will **open up a shell with a virtual environment that has the right version of Python and the right packages**.

## Install pyenv and poetry

### Linux/Raspbian

- See [4 - Install Project Specific Packages](https://github.com/alfondehesa/RPi_Project_Starter/blob/main/4%20-%20Install%20Project%20Specific%20Packages%20(Python).md).

### Windows (for your IDE)

- [ ] Before getting started, you will first need to **allow running scripts in your Shell**.
  - [ ] Open **Windows PowerShell** as an **administrator**.
  - [ ] **Run**: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned`.
  - [ ] **Select yes** `[Y]` to allow scripts to be run in your machine.

> [!NOTE]
> *You can change this back to no `[N]` after having installed the packages, for security reasons.*

#### Install Pyenv

- [ ] **Run**: `Invoke-WebRequest -UseBasicParsing -Uri "https://raw.githubusercontent.com/pyenv-win/pyenv-win/master/pyenv-win/install-pyenv-win.ps1" -OutFile "./install-pyenv-win.ps1"; &"./install-pyenv-win.ps1"`.
- [ ] **Close and open the terminal** (also close and open your IDE).
- [ ] **Run** `pyenv --version` to check that the **installation was successful** and that you have a version of pyenv in your machine.

> [!NOTE]
> *For pyenv to work properly, you might have to uninstall other Python environment managers if you have any installed.*

#### Install Poetry

- [ ] Before installing poetry, you will **need a version of Python**. Any version will do. We will use pyenv to download one and set is as the global system version.
  - [ ] **Run**: `pyenv install -l`. This will display a list of all **available versions of Python** to install.
  - [ ] **Run**: `pyenv install 3.11.4`.
  > [!NOTE]
  > *At the time of writing, the latest stable build is `3.11.4`, so we will install this one. You can install any version, however.*
  - [ ] Now set is as the **global default**, for this, **run**: `pyenv global 3.11.4`.
  - [ ] Verify this is set correctly, **run**: `pyenv versions`, make sure `3.11.4` is there and is **highlighted with an asterisk `*`**, denoting it as the **global Python installation**.

> [!NOTE]
> *Now, when you type `python` in any command window in your system, a new `Python 3.11.4` shell will open. You can close it by typing `exit()`.*
> *This is the version that will run by default in any directory if you have not selected a local version.*

- [ ] **Run**: `(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | python -`.

- [ ] We now need to add **Poetry** to our `PATH`, to make sure it can be **called everywhere**. To do so:
  - [ ] On install, **Poetry** will give you it's `bin` directory and prompt you to **add it to your `PATH`**.
  > [!NOTE]
  > *At the time of writing, for me, it was `C:\Users\YOUR_USER_NAME\AppData\Roaming\Python\Scripts`, but keep in mind that this might change over time, so you should always pick the one that was given to you upon install.*
  - [ ] On the **windows search bar**, **type `Environment Variables`** and click on **`Edit the system environment variables`**.
  - [ ] Click on **`Environment Variables...`**.
  - [ ] Under **`System Variables`**, select **`Path`**.
  - [ ] Click on **`Edit...`**.
  - [ ] In the new window that opened, click on **`New`**. **Paste whatever path poetry gave you** on installation.
  - [ ] Click on **`Ok`** on both windows.
  - [ ] **Restart** your machine.
  - [ ] **Run** `poetry --version` to check that the installation was **successful** and that you have a version of Poetry in your machine.

> [!IMPORTANT]
> It is highly recommended you run this option change now: `poetry config virtualenvs.in-project true`. This will prompt Poetry to install your virtual environment in the project directory itself, rather than on your machine. This virtual environment is still specific to your machine and will be ignored by git. There are advantages and drawbacks to enabling this option. One of the advantages is that, when deleting the project directory, you will delete all the dependencies with it, thus not cluttering your machine with virtual environments.

### Other OS

- [ ] Refer to the following guides:
  - [ ] [Install `pyenv`](https://github.com/pyenv/pyenv#installation).
  - [ ] [Install `poetry`](https://python-poetry.org/docs/).

## Start a project with pyenv and poetry

### From Linux/Debian/Raspbian

- [ ] `cd` to your **project directory**.
- [ ] Make sure you have **installed the version of Python you want to use** for your project: run `pyenv versions`.

> [!NOTE]
> *Else, run `pyenv install -l` for a list of available Python versions, and `pyenv install THE_PYTHON_VERSION` to install your desired version (change `THE_PYTHON_VERSION` for your desired version, such as `3.11.4` or similar).*

- [ ] We can now **run** `poetry init`. This interactive initialization procedure will guide you through **adding your initial Python version and package dependencies**.
- [ ] You can now **run** `poetry shell` to start a **Python shell**. Poetry will first create a **virtual environment** (it will do so in the project directory if you set the option prior). To do so, it will look for **whichever version of Python you specified** when running the initialization procedure, and if it is not in your system, will **prompt you to install it** (you can use pyenv). Then, once it finds the version of Python, it will start a new shell with your virtual environment.
- [ ] You can add and **install dependencies with `poetry add PACKAGE_NAME@*`**. You can change `PACKAGE_NAME` for your specific package name. In case on package name ambiguity, **poetry will prompt you to select the desired package**. The trailing `@*` is not necessary, and it is used to **specify a version**. For instance, `poetry add numpy@11.2` will install `numpy 11.2` and add it to your dependency file. By leaving an asterisk `@*` you are **specifying the latest version that is compatible with all other dependencies**, thus making it a good practice to use it.

### From Windows (VS Code)

- [ ] Open a **PowerShell terminal** in your **project directory**.
- [ ] Make sure you have **installed the version of Python you want to use** for your project: run `pyenv versions`.

> [!NOTE]
> *Else, run `pyenv install -l` for a list of available Python versions, and `pyenv install THE_PYTHON_VERSION` to install your desired version (change `THE_PYTHON_VERSION` for your desired version, such as `3.11.4` or similar).*

- [ ] We can now **run** `poetry init`. This interactive initialization procedure will guide you through **adding your initial Python version and package dependencies**.
- [ ] You can now **run** `poetry shell` to start a **Python shell**. Poetry will first create a **virtual environment** (it will do so in the project directory if you set the option prior). To do so, it will look for **whichever version of Python you specified** when running the initialization procedure, and if it is not in your system, will **prompt you to install it** (you can use pyenv). Then, once it finds the version of Python, it will start a new shell with your virtual environment.
- [ ] You can add and **install dependencies with `poetry add PACKAGE_NAME@*`**. You can change `PACKAGE_NAME` for your specific package name. In case on package name ambiguity, **poetry will prompt you to select the desired package**. The trailing `@*` is not necessary, and it is used to **specify a version**. For instance, `poetry add numpy@11.2` will install `numpy 11.2` and add it to your dependency file. By leaving an asterisk `@*` you are **specifying the latest version that is compatible with all other dependencies**, thus making it a good practice to use it.

## Open a project with pyenv and poetry

### Opening from Linux/Debian/Raspbian

- [ ] `cd` to your **project directory**.

> [!NOTE]
> *If you still need to clone the repo, you can `gh repo clone`. For more information, visit [5.1 - Using GitHub](https://github.com/alfondehesa/RPi_Project_Starter/blob/main/5.1%20-%20Using%20Github.md).*

- [ ] If your project already has a **poetry environment ready**, you can **use `poetry shell` to attempt to launch a shell** in your virtual environment.

> [!WARNING]
> Poetry might warn you to **install the right version of Python** if you haven't already. To do so, use **Pyenv: `pyenv install VERSION_OF_PYTHON`** (replace `VERSION_OF_PYTHON` by the version suggested by Poetry).

- [ ] Once in the **shell**, use **`poetry install` to install all the right dependencies**.
- [ ] **That's it**! You can now execute your project from the shell having all the right dependencies.

### Opening from Windows (VS Code)

- [ ] **Open or clone** your project using **VS Code**.
- [ ] **Open a terminal** PowerShell instance on your project.
- [ ] If your project already has a **poetry environment ready**, you can **use `poetry shell` to attempt to launch a shell** in your virtual environment.

> [!WARNING]
> Poetry might warn you to **install the right version of Python** if you haven't already. To do so, use **Pyenv: `pyenv install VERSION_OF_PYTHON`** (replace `VERSION_OF_PYTHON` by the version suggested by Poetry).

- [ ] Once in the **shell**, use **`poetry install` to install all the right dependencies**.
- [ ] **That's it**! You can now execute your project from the shell having all the right dependencies.

#### Use Poetry as default Python interpreter

Additionally, you **should also set your Poetry virtual environment** as the **default interpreter** for your project, to be able to run it straight without starting a poetry shell.

- [ ] To do so, **use `Ctrl + Shift + P`** to open the **VS Code command bar**, and **type `Python Interpreter`**. Select the **local `.venv` poetry interpreter** (*which should appear after you have opened a `poetry shell` at least once, as Poetry will automatically install the virtual environment as you do so*).
- [ ] **That's it**! You can now execute your project directly from VS Code having all the right dependencies.

## Manage dependencies

- [ ] **Start to manage a repo** with Poetry with `poetry init`.
- [ ] You can **add a library** with `poetry new <library>@*`.
- [ ] You can **remove a library** with `poetry remove <library>`.
- [ ] **Run outside of Poetry Shell** with `poetry run python app.py`.
- [ ] **Show dependencies** with `poetry show`.
- [ ] **Lock dependencies** with `poetry lock`.
- [ ] **Spawn a shell** in the project's virtual environment with `poetry shell`.
- [ ] **Update dependencies** with `poetry update`.

## Next Steps

**That is it for this guide**! You are now ready to **start a project by creating a Python file**!
