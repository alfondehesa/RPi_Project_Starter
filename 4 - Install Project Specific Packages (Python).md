# 4 - Install Project Specific Packages (Python)

## Table of contents

- [ ] [Summary](4%20-%20Install%20Project%20Specific%20Packages%20(Python).md#summary)
- [ ] [Install pyenv](4%20-%20Install%20Project%20Specific%20Packages%20(Python).md#install-pyenv)
- [ ] [Install rust (prerequisite for poetry)](4%20-%20Install%20Project%20Specific%20Packages%20(Python).md#install-rust-pre-requisite-for-poetry)
- [ ] [Install poetry](4%20-%20Install%20Project%20Specific%20Packages%20(Python).md#install-poetry)
- [ ] [Install git](4%20-%20Install%20Project%20Specific%20Packages%20(Python).md#install-git)
- [ ] [Install gh](4%20-%20Install%20Project%20Specific%20Packages%20(Python).md#instal-gh)
- [ ] [Next Steps](4%20-%20Install%20Project%20Specific%20Packages%20(Python).md#next-steps)

## Summary

We will now install some **packages** that we will need to manage our **python project**.

### Pyenv

- We will **install** `pyenv` to manage our **python environments** and **versions**.
  
- `pyenv` is used to **isolate a python installation and version**, and tie it to a specific project, so that the **project will work regardless of what version of python you use** in general in your system, or in your other projects (that might have other environments).

### Poetry

- We will also **install** `poetry`.
  
- `poetry` is a **package manager**, that specifies your **project dependencies** so that other users can **install the exact same packages and versions** of which you used in your project.

- For instance, if your project needs a **certain version** of `numpy`, and is **only compatible with that version**, `poetry` will allow users to **automatically install `numpy` with the specific version,** to guarantee your project will run correctly in their system.

### Git and gh

- We will also **install** `git`, and `gh`.

- `git` is a **file manager** that focuses on the **handling and versioning of code repositories**. A code **repository** is a **virtual directory** where your code can be **stored and shared**.

- We will use **GitHub** as the server that will house our **code repository** for this project. We will use `git` to **sync our local files with the GitHub repository**.

- `gh` is a **package** that focuses on handling **GitHub features** through the terminal. We can use it in case we want to **remotely access GitHub features** (like pull requests, complex merges, being social, etc.) without the need for a browser, straight from our Pi's **UNIX-based terminal**.

## Install pyenv

- [ ] **Run**: `curl https://pyenv.run | bash`.

- [ ] We need to **add `pyenv` to our `bashrc` file**, to let the package be **called anywhere** in the system (without needing to be in the program's folder). This is called and **environment variable**. To do so:

  - [ ] **Run**: `nano ~/.bashrc`.
    > [!NOTE]
    > *This opens your `bashrc` file in a text editor.*

  - [ ] Anywhere in the file, **add the following lines**:
  
  ```bash
  export PATH="~/.pyenv/bin:$PATH"
  eval "$(pyenv init -)"
  eval "$(pyenv virtualenv-init -)"
  ```

  - [ ] `Ctrl + O` and `Enter` to **save**, and `Ctrl + X` to **exit**.
  
  - [ ] **Run**: `source ~/.bashrc`.
    > [!NOTE]
    > *This reloads the `bashrc` file in the system.*

## Install Rust (prerequisite for poetry)

- [ ] **Run**: `curl --proto '=https' --tlsv1.3 https://sh.rustup.rs -sSf | sh`.

- [ ] Follow the **instructions** on the **prompt**.

- [ ] Add `rust` as an **environment variable**, to do so:

  - [ ] **Run**: `source $HOME/.cargo/env`.

  - [ ] **Run**: `source ~/.bashrc`.
    > [!NOTE]
    > *This reloads the `bashrc` file in the system.*

## Install Poetry

- [ ] Before installing poetry, you will **need a version of Python**. Any version will do. We will use pyenv to download one and set is as the global system version.
  - [ ] **Run**: `pyenv install -l`. This will display a list of all **available versions of Python** to install.
  - [ ] **Run**: `pyenv install 3.11.4`.
  > [!NOTE]
  > *At the time of writing, the latest stable build is `3.11.4`, so we will install this one. You can install any version, however.*
  - [ ] Now set is as the **global default**, for this, **run**: `pyenv global 3.11.4`.
  - [ ] Verify this is set correctly, **run**: `pyenv versions`, make sure `3.11.4` is there and is **highlighted with an asterisk `*`**, denoting it as the **global Python installation**.

- [ ] Now, we are ready to install Poetry. **Run**: `curl -sSL https://install.python-poetry.org | python3 -`.

  > [!WARNING]
  > If this does **not work**:
  >
  > - **Option 2**:
  >   - **Run**: `apt-get install pipx`.
  >   - **Run**: `pipx install poetry`.
  >
  > - **Option 3**:
  >   - **Run**: `pip install poetry`.
  >   - **Follow [the instructions here](https://python-poetry.org/docs/#installing-manually).**

- [ ] We need to **add `poetry` to our `bashrc` file**, to let the package be **called anywhere** in the system (without needing to be in the program's folder). This is called **adding to your PATH**. To do so:

  - [ ] **Run**: `nano ~/.bashrc`.
    > [!NOTE]
    > *This opens your `bashrc` file in a text editor.*

  - [ ] Anywhere in the file, **add the following line** (replace `YOUR_USER_NAME` for your username without crochets): `export PATH="/home/[YOUR_USER_NAME]/.local/bin:$PATH"`.

  - [ ] `Ctrl + O` and `Enter` to **save**, and `Ctrl + X` to **exit**.

  - [ ] **Run**: `source ~/.bashrc`.
    > [!NOTE]
    > *This reloads the bash file in the system.*

  - [ ] **Run** `poetry --version` to check that the installation was **successful** and that you have a version of Poetry in your machine.

> [!IMPORTANT]
> It is highly recommended you run this option change now: `poetry config virtualenvs.in-project true`. This will prompt Poetry to install your virtual environment in the project directory itself, rather than on your machine. This virtual environment is still specific to your machine and will be ignored by git. There are advantages and drawbacks to enabling this option. One of the advantages is that, when deleting the project directory, you will delete all the dependencies with it, thus not cluttering your machine with virtual environments.

## Install git

- **Run**: `sudo apt-get install git-all`.

## Install gh

- **Run**:

```BASH
type -p curl >/dev/null || (sudo apt update && sudo apt install curl -y)
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg \
&& sudo chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg \
&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
&& sudo apt update \
&& sudo apt install gh -y`.
```

## Next Steps

- Create a **git repository**.

  - Go to [5 - Create a git repository](5%20-%20Create%20a%20git%20repository.md).

- [Back to README](README.md).
