# 3 - Install necessary packages

## Summary

To **start the project**, there are some **packages we are going to need**. We will use `apt-get`, which is **Linux's package installer**. This guide will walk you through **installing them**.

## Installing packages

- [ ] **Update** `apt-get` and **package index**.
  - Run:

    ```bash
    sudo apt-get update && sudo apt-get upgrade -y
    ```

- [ ] **Install packages**.
  - Run:

    ```bash
    sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python3-openssl openssl bzip2 git lzma libbz2-dev
    ```
  
  - **Some packages will be installed**.

## Next Steps

- Install project specific packages for python.

  - Go to [4 - Install Project Packages (Python)](4%20-%20Install%20Project%20Specific%20Packages%20(Python).md).

- [Back to README](README.md).
