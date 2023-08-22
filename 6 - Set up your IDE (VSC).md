# Set up your IDE (VSC)

## Table of contents

- [ ] [Summary](6%20-%20Set%20up%20your%20IDE%20(VSC).md#summary)
- [ ] [Install VS Code](6%20-%20Set%20up%20your%20IDE%20(VSC).md#install-vs-code)
- [ ] [Navigate VS Code](6%20-%20Set%20up%20your%20IDE%20(VSC).md#navigate-vs-code)
- [ ] [Working with git](6%20-%20Set%20up%20your%20IDE%20(VSC).md#working-with-git)
- [ ] [Install plugins](6%20-%20Set%20up%20your%20IDE%20(VSC).md#install-plugins)
- [ ] [Start a project](6%20-%20Set%20up%20your%20IDE%20(VSC).md#start-a-project)
- [ ] [Next Steps](6%20-%20Set%20up%20your%20IDE%20(VSC).md#next-steps)

## Summary

- If your project is anything **larger than a few lines of code**, you will most likely **not be able to develop it efficiently** by creating and adding to files on your Pi or directly online through [GitHub's website](https://github.com/).

- That's where **IDE**s come in to play. **IDE**, or **Integrated Development Environment**, is a piece of software that you usually install in your main computer, that allows you to **develop software in a more efficient manner**.

- They have tools and capabilities that **significantly speed up development**. A few of which can be:

  - **Linting**, which is dynamic markdowns of errors or style inaccuracies in your code as you write.
  - **Debugging**, which allows you to test out your code, and identify and fix unexpected behaviors before you publish it.
  - **Autocompletion**, which gives you suggestions as you type.
  - **Many shortcuts** that make writing significantly faster.

- For **Python projects**, there seem to be 2 major popular IDEs that most developers use, **PyCharm**, and **VS Code**.

### PyCharm

**PyCharm** is an **IDE** specifically designed from the ground up to work with **Python**.

#### The good of PyCharm

- Has a clean and intuitive **GUI**.
- The **code completion, code analysis and refactoring tools** for **Python** are **top-notch**.
- **Debugging is much easier** in PyCharm.
- It has a **built-in Python learning tool**.

#### The not so good of PyCharm

- It is **not prepared to work with languages other than Python**.
- Some features are **pay-walled**.
- **Heavier** than alternatives, and **high CPU consumption**.
- **Less used than other IDEs** means less available plug-ins.
- Does not support new Python features as quickly as other IDEs.

### VS Code

*Visual Studio* Code is a **code editor** made by **Microsoft**.

#### The good of VS Code

- **Lightweight** and **fast**.
- Works well for **almost all languages**, making it the **top choice** if your **project uses more than one language**, or if you are planning on **learning more than one language**.
- Intuitive user **GUI**.
- The **code completion, code analysis and refactoring tools** for **most languages** are **top-notch**.
- It is **completely free and open source**.
- It is **widely used**, and it has the largest amount of plug-ins and third party customization options available.

#### The not so good of VS Code

- Lots of functionality means it is **not the most beginner-friendly**.
- **Debugging tools are not the most intuitive**.
- **Less Python specific features** than PyCharm.
- Does **not work out-of-the-box with all programming languages**, you will have to install plugins to bring in functionality.

### This guide

For this guide, we will install and run **VS Code**, as it will allow the user to **easily learn and use as many languages as desired**.

## Install VS Code

- [ ] Go to [**VS Code's Website**](https://code.visualstudio.com/).

- [ ] **Download and install** the latest stable build for your operating system.

- [ ] **Open** VS Code.

- [ ] **That's it**!

## Navigate VS Code

This guide will get you **up to speed** on how to **use and navigate VS Code**.
On the **leftest** most part of your screen, you will find the **activity bar**. This is used to **navigate different functions** and aspects of your project.

### File Explorer

The **first** icon the activity bar is your **file explorer**, which will help you **navigate and open all files in your project directory**.

If you **click on one of these files**, a **tab opens** in the **center of the screen**. What you are looking at is your **workspace**.

Here, you can **open as many tabs as you want** to work on as many files as you want. It also supports **dynamic previews for HTML files** and the such. You can switch back and forth between opened files by clicking on the **file tab**.

As you create a **new file in the file explorer activity tab**, and you type something, in your **workspace**, you will notice a **dot on the file's tab**. This is **VS Code letting you know that the file in question has not been saved**, and so closing it would **lose your changes**. You can **save** by using `Ctrl + S`. You can also **enable `autosave` on the file tab of the menu bar** (all the way up to the left). This will **autosave changes as you make them**.

### Search tab

The **second** tab in your activity bar is the **search tab**. This will search **any file if your project directory** for whatever you type in it.

### Git

The **third** icon in your activity bar is the **Git menu**. For this, **VS Code will most likely ask you to install git into your computer** if you don't have it already. On the Git tab, you can **create, upload, and clone repositories to and from GitHub**, as you would in a command line interface, but with a **GUI** instead. This makes it so that you **don't have to leave VS Code to push code or create commits** (or in reality, almost any activity that you would either do on GitHub or through CLI).

The most common workflow you will do here is **stage all changes to the repo you are working on, commit the changes, and push the changes to GitHub**.
  
It will also **allow you to deal with merge conflicts as you do so**.

### Debugging

The **fourth** icon in your icon tab is the **debugging menu**. This will allow you to **debug your code**. For more info on how to do this, you can visit [this guide](https://code.visualstudio.com/docs/editor/debugging).

### Plugins

The **fifth** icon in the lineup is the **plugins icon**. This is where you will **download plugins to extend VS Code's functionality**.

### Remote explorer

The **sixth** is the **remote explorer**, which allows you to use **VS Code through a remote host**.

### Panel

**Underneath your workspace**, you will find **the panel**. Here, you will see a **wholistic analysis of every problem found in your repository, an output console, a dedicated debug console, terminals you can open** (from PowerShell, to cmd, git, or even WLI if you have it installed), **and even workspace comments**.

## Working with git

The **first time** you open the **git activity tab**, you will be prompted to install `git`.

- [ ] **VS Code** will prompt you to open [git's website](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git). Download and install `git` from there.

- [ ] As you go through the installation process, `git` will **automatically be added to the path environment variable**.

> [!NOTE]
> *As you go through the installation process, `git` will automatically be added to the path environment variable.*
> *You will also be able to open `git bash` through VS Code, on the terminal tab of the panel, by clicking on the plus icon and selecting `git bash`.*

- [ ] **Open a git bash console** (you can do this directly on VS Code, or you might be able to use the `git` command on the PowerShell in windows).

- [ ] We will now **set VS Code as the default git text editor**. For this, **run**: `git config --global core.editor "code --wait"`.

- [ ] We will also ne**ed to sign in to git with our username and email**, for this, **run**: `git config --global user.name "Your Name" && git config --global user.email "your_email@example.com"`. **Change `Your Name` and `your_email@example.com` for your own username and email** (that you use for GitHub). Leave the quotes `""`.

- As you try to **clone your first repo**, `git` will prompt you to sign in with **GitHub**. It will open a browser window where you can do so.

## Install plugins

These are some **general plugins** to **extend the functionality of VS Code**.
Keep in mind that to have **linting, suggestions and more in VS Code for Python**, you will have to **install Python specific plugins**.

### Needs

- [ ] **Python by Microsoft**: *this will add support and lots of features for managing Python projects in VS Code, including linting, suggestions, Jupiter Notebooks and even a Python terminal.*

### Python specific nice-to-haves

- [ ] **Black Formatter**: *Black formatter is a code formatter (it does not change your code itself, it will just change its appearance) that will re-organize your code to adhere to the "Black" style guide. This is a Python style that is adopted by many Python developers, and although it is not tweakable, it makes up for it in consistency, and allows you to not waste your time making your code look pretty. Now you have a tool that does that, and makes all the decisions for you!*

  > [!NOTE]
  > *You can now press `Shift + Alt + F` when on a Python file to automatically format it.*
  > *Alternatively, on your user settings, you can activate `Format on Save` to format your code automatically as you save it.*

- [ ] **Pyrefact**: *Pyrefact is a refactoring tool for Python. Unlike the Black Formatter, Pyrefact actually changes your code to make it both easier to read, but also less computationally expensive. It can do things such as convert loops into constants, un-indent nested code, and remove dead code. Unlike Black, Pyrefact might break your code, as it does change the fundamental functioning of it. You can find a list of [all Pyrefact can do here](https://github.com/OlleLindgren/pyrefact-vscode-extension).*

  > [!NOTE]
  > *To use it, right-click on your file, and select `format with`, and choose Pyrefact.*

- [ ] **Isort**: *Sorts your imports using isort*.

### General nice-to-haves

#### Git Plugins

- [ ] **GitHub Pull Requests and Issues**: *Lets you view and merge pull requests from VS Code*.

- [ ] **GitHub Lens**: *One-stop shop for inspecting GitHub branches, commits, issues, etc*.

#### Others

- [ ] **Indent-rainbow**: *Colors indentations so that you can keep better track of your indentations*.

- [ ] **IntelliCode**: *Shows you AI assisted code suggestions as you type, also finds good examples of suggestions on GitHub*.

- [ ] **Remote - SSH**: *Uses SSH to connect to a remote machine as if it was another project directory! This means you will be able to remotely view and edit any files in your Pi directly from VS Code*.

- [ ] **Code Spell Checker**: *Spell checks your code*.

## Start a project

### From scratch

- [ ] Open a new folder.
- [ ] Right click on file editor.
- [ ] Create a file.
- [ ] Done!

### Clone a repo

- [ ] Go to the git activity tab.
- [ ] Click clone a repo.
- [ ] Follow the prompts on screen.
- [ ] Done!

## Next Steps

- Use pyenv and poetry to set up and use your python environment for your repository.

  - Go to [7 - Use pyenv and poetry to set up and use your python environment](7%20-%20Use%20pyenv%20and%20poetry%20to%20set%20up%20and%20use%20your%20python%20environment.md).

- [Back to README](README.md).
