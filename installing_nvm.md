# Node Version Manager (NVM)

> *Last updated on **11/22/2022***
>
> Node Version Manager - POSIX-compliant bash script to manage multiple active node.js versions

- [Node Version Manager (NVM)](#node-version-manager-nvm)
  - [NVM install script](#nvm-install-script)
    - [Verify Installation](#verify-installation)
  - [Add Bash Function](#add-bash-function)
    - [Install `cowsay` via Homebrew](#install-cowsay-via-homebrew)

Official documentation found at <https://github.com/nvm-sh/nvm>.

Do **not** install Node.js directly (by downloading OS specific installer from Node.js website.)

We use NVM, `.nvmrc` files, and a bash function to lock down the Node.js version of each individual project.

-----

## NVM install script

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash
```

### Verify Installation

You should completely exit all terminal instances and quit whichever terminal program or app you are using. Restart your preferred terminal and run the following command:

```bash
command -v nvm

## If working properly it will return the following:
nvm
```

-----

## Add Bash Function

If you group and organize your dotfiles, add the following to your `.functions` file, otherwise place the following snippet in one of you bash initialization files.

**This bash function requires `cowsay`.**
See [Install `cowsay` via Homebrew](#install-cowsay-via-homebrew) for more information.

```bash
## Use a local .nvmrc file if present
enter_directory() {
  if [[ $PWD == $PREV_PWD ]]; then
    return
  fi

  PREV_PWD=$PWD
  [[ -f ".nvmrc" ]] && nvm use > /dev/null 2>&1 && nvm use | cowsay $n
}

export PROMPT_COMMAND=enter_directory
```

### Install `cowsay` via Homebrew

Our bash function utilizes `cowsay` to create a more aesthetically pleasing console output.

It can be installed using **Homebrew**:

```bash
brew install cowsay
```

See [Install Homebrew](./installing_rvm/#install-homebrew) (in our RVM documentation.)

-----

[Back to main README](../)
