# 5 - Create a git repository

Although this step is **optional**, it is **highly recommended** you set up a **GitHub repository** for your project. This will enable you to **version track your code, make improvements in a non-destructive way, collaborate and be able to use any workstation of your choice** easily instead of having to write code in the Pi.

## Table of contents

- [ ] [Summary](5%20-%20Create%20a%20git%20repository.md#summary)
- [ ] [Before getting started](5%20-%20Create%20a%20git%20repository.md#before-getting-started)
- [ ] [Start a repository online (RECOMMENDED)](5%20-%20Create%20a%20git%20repository.md#start-a-repository-online-recommended)
- [ ] [Start a repository locally (NOT RECOMMENDED)](5%20-%20Create%20a%20git%20repository.md#start-a-repository-locally-not-recommended)
- [ ] [Next Steps](5%20-%20Create%20a%20git%20repository.md#next-steps)

## Summary

### What is a repo, and what is a GitHub repository?

- A **repo** is a **directory** that is **specifically destined to host code**.

- Unlike regular storage, **repos** often come with a suite of **tools that make managing code easier**, such as branches, versioning, tracking changes (and committing), forking, pull requests, among many others.

- `git` is a **library that specializes in creating repositories**.

- **GitHub** offers **online storage for repositories** that use the `.git` platform.

- We will use `git` to **create and manage our repository locally**, and we will use **GitHub** to **host our repository online**.

### Pi's root and home directories

- Where should you store the repository locally at the Pi? Although any directory is valid, users often store **repositories** in either their **home directory**, or the **root directory** of a Raspberry Pi.

- If you run the `cd` command in the `ssh` prompt, it will take you to your **personal user home directory**, which is abbreviated with a `~` symbol.

- If you haven't signed in as a user, it will just take you to the **general home directory**.

- You can check the directory you are in at any time by running `pwd` (print working directory), and it will return something like: `/home/monalisa`.

- If you want to go to the **Pi's root directory** (parent most directory), you can instead run `cd /`.

- For this project, we will start a repo in our **home directory**.

### Ways of starting a repository

- There are **two main ways to create a repo**, on GitHub's website, or directly on the Pi.

- Either is a good option, but **[cloning the repository once it is created online at GitHub's website](5%20-%20Create%20a%20git%20repository.md#start-a-repository-online-recommended) is easiest**.
  
- This is because GitHub has a GUI method of creating new repos, and cloning repositories handles setting origin upstream branches automatically, whereas creating them locally requires doing so as an extra step.

- Of course, if you choose to **[start a repository on the Raspberry Pi](5%20-%20Create%20a%20git%20repository.md#start-a-repository-locally-not-recommended)**, you will not need a browser, which is an added bonus.

## Before getting started

There are a **couple of steps we need to do** before getting started.

### Sign in

> [!IMPORTANT]
>
> **It is important to initialize `git` and `gh` by setting some prior parameters.**
>
> - [ ] **Sign in to GitHub by running `gh auth login` and following the instructions on the prompt.**
> - [ ] **Declare your email by running `git config --global user.email "you@example.com"` (replace with your email, leave the quotes `""`).**
> - [ ] **Declare your username by running `git config --global user.name "Your Name"` (replace with your name, leave the quotes `""`).**

### Set `main` as default

> [!IMPORTANT]
>
> - **Git uses "master", and GitHub uses "main" by default to refer to the main branch of your repository.**
> - **This can cause problems down the line (mismatch on push/pulls, etc.).**
> - **To fix this, we will let git know to always use "main" as the default branch when creating new repositories.**
>   - **On the Pi, run: `git config --global init.defaultBranch main`**

## Start a repository online (RECOMMENDED)

We will **create the repository online, and clone it locally**.

- [ ] [Create a GitHub repository from a browser](https://docs.github.com/en/get-started/quickstart/create-a-repo?tool=webui)

- [ ] `cd` to your **home directory**, **run**: `cd`

- [ ] **Create a folder** where you will contain this repo, and other related repos, **run**: `mkdir the_name_of_your_folder`

- [ ] `cd` to this new folder, **run**: `cd the_name_of_your_folder`

- [ ] **Confirm you are on your folder**, located on your user folder in the **home directory**, **run**: `pwd`

- [ ] **Clone your online repo**, to do so, **run**: `gh repo clone https://github.com/your_user_name/your_repo_name`. **Substitute** `your_user_name` and `your_repo_name` for your **own values**.

> [!NOTE]
>
> - *This will essentially set up a local directory that is connected to the online repo, so that when you either push or pull, it pushes and pulls changes to and from online.*
> - *In this case, it also downloads a full copy of the repository, and creates the local main branch for you also.*

## Start a repository locally (NOT RECOMMENDED)

- [ ] `cd` to your **home directory**, **run**: `cd`

- [ ] **Create a folder** where you will contain this repo, and other related repos, **run**: `mkdir the_name_of_your_folder`

- [ ] `cd` to this new folder, **run**: `cd the_name_of_your_folder`

- [ ] **Confirm you are on your folder**, located on your user folder in the **home directory**, **run**: `pwd`

- [ ] **Run**: `gh repo create`

- [ ] **Follow the prompted instructions** (give the repo a name, set the settings, add a README file if you want)

- [ ] When it prompts you to **clone the repo** on your local machine, say **yes**.
  > [!NOTE]
  >
  > - *This will essentially set up a local directory that is connected to the online repo, so that when you either push or pull, it pushes and pulls changes to and from online.*
  > - *However, it does not initially download any files in the new repo (any changes), nor does it create any local branch.*

- [ ] If you **run**: `git branch -a`, it will show you **all the branches in your repo**, which currently, since you haven't synced the repo yet, **you should have none**.

- [ ] To download everything from the repo, **run**: `git pull`

- [ ] If you now **run**: `git branch -a` again, it will show you the **online `main` branch**, as `remotes/origin/main`. It shows this **remote branch in red**. We need to make a local branch that mirrors the online main branch.

- [ ] Git will only make a local branch once you have something to commit (otherwise, why have a branch at all?). We need to make a **meaningless change to prompt git to create a local version of `main`**.
  
  - [ ] **Run**: `touch newfile` to **create an empty file**.

  - [ ] Then, **run**: `git add .` to **add all files** (including `newfile`) **to the repo index** (essentially telling GitHub that this new file is going to be part of the repo).

  - [ ] **Run** `git commit -m "Initial Commit"` to **create your first commit**.

- [ ] If you now **run**: `git branch -a` you will notice you have a **local `main` branch (colored green)**. We have to now tell the Pi that this local branch corresponds to the remote main branch of the repository. We will tell the Pi to **merge the remote main branch**, to our local main branch, and to **tie these two branches together** from now on, all in one step.

  - [ ] **Run**: `git pull --set-upstream --allow-unrelated-histories origin main`. It might ask you to give a reason for the commit, but you don't have to, just exit the text editor.

- [ ] Now, **run**: `git push` to **update the changes to the remote branch**, to what you have currently in your branch.

- [ ] You might now choose to **delete the file you created** and `push` the changes again to GitHub, see [4.1 - Using GitHub](5.1%20-%20Using%20GitHub.md).

## Next Steps

- Learn to **navigate git and GitHub**.

  - Go to [5.1 - Using GitHub](5.1%20-%20Using%20Github.md).

- Set up a self **updating local repository** in your Pi.

  - Go to [5.2 - Set up a self updating local repository](5.2%20-%20Set%20up%20a%20self%20updating%20local%20repository.md).

- Add a **local repository to self update** to an already set up self updating Raspberry Pi.

  - Go to [5.3 - Add a repo to self update](5.3%20-%20Add%20a%20repo%20to%20self%20update.md).

- Alternatively, you can skip the previous steps and go straight to **setting up your IDE**.

  - Go to [6 - Set up your IDE (VSC)](6%20-%20Set%20up%20your%20IDE%20(VSC).md).

- [Back to README](README.md).
