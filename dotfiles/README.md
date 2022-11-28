# Setting Up Dotfiles

> *Last updated on **11/28/2022***

- [Setting Up Dotfiles](#setting-up-dotfiles)
  - [Load Custom Dotfiles in `.bash_profile`](#load-custom-dotfiles-in-bash_profile)
  - [`.functions`](#functions)
  - [`.aliases`](#aliases)
    - [Folder Navigation](#folder-navigation)
    - [Git](#git)
    - [Other](#other)

This document covers setting up dotfiles for `bash` and adding some helpful functions and aliases.

These functions and aliases are designed to make common tasks and commands easier and quicker when working in terminal (bash).

-----

## Load Custom Dotfiles in `.bash_profile`

To use custom `.aliases` and `.functions` files you need to load them in your `.bash_profile`.

Add the following to your `.bash_profile`:

```shell
# ~/.bash_profile

for file in ~/.{bash_prompt,aliases,functions}; do
        [ -r "$file" ] && [ -f "$file" ] && source "$file";
done;
unset file;
```

Other dotfiles may be added in the for..in loop's curly braces. This example includes another `.exports` dotfile:

```bash
# ~/.bash_profile

for file in ~/.{bash_prompt,aliases,exports,functions}; do ## Added exports
        [ -r "$file" ] && [ -f "$file" ] && source "$file";
done;
unset file;
```

-----

## `.functions`

The `dotfiles/` directory of this project contains a `.functions` file which contains the `enter_directory` function covered here.

We use the following function — and `.nvmrc` files in each project's root — to lock down the version of Node.js on a per-project basis.

This `enter_directory()` function works every time you change directories. It checks for a local `.nvmrc` file and, if it finds one, runs the `nvm use` command. 

Without this function, you would need to remember to run `nvm  use` manually every time you `cd` into a new project with an `.nvmrc` file.

**This bash function requires `cowsay`.**
See [Install `cowsay` via Homebrew](./installing_nvm.md#install-cowsay-via-homebrew) for more information.

```bash
# ~/.functions

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

-----

## `.aliases`

The `dotfiles/` directory of this project contains an `.aliases` file which has all of these aliases already.

### Folder Navigation

```bash
# Easier navigation: .., ..., ...., ....., ~ and -
alias ..="cd .."
alias ...="cd ../.."
alias ....="cd ../../.."
alias .....="cd ../../../.."
alias ~="cd ~" # `cd` is probably faster to type though
alias -- -="cd -"
alias back="cd $OLDPWD"

# Shortcuts
alias d="cd ~/Documents"
alias dl="cd ~/Downloads"
alias dt="cd ~/Desktop"
alias r="cd ~/repositories"
```

### Git

```bash
## Git Aliases
alias g="git"
alias gb="git branch"                       # alias for git branch
alias gs="git status"                       # alias for git status
alias ga="git add"
alias gc="git commit"
alias gl="git log"
alias glo="git log --pretty=online"
alias glu="git log --pretty=format: '%h %ad | %s%d [%an]' --graph --date=short"
alias go="git checkout"
alias gt="git tag"
alias grs="git reset"
alias grv="git revert"
alias gf="git fetch"
alias gm="git merge"
alias gpom="git push -u origin master"
alias gpum="git pull origin master"
alias gd="git diff"                         # alias for git diff
alias gpo="git push origin"
alias gob="git checkout -b"

# My custom git aliases for working with a publish branch (i.e. CloudCannon setup for publishing workflow)
alias gpop="git push -u origin publish"
alias gop="git checkout publish"
alias gom="git checkout master"
alias gpu="git pull"
alias gmp="git merge publish"
alias gmm="git merge master"

# Undo a 'git push'
alias undopush="git push -f origin HEAD^:master"

# Stop git from tracking an already cached & tracked file
# Usage:`uncache <FILE_NAME>`
alias uncache="git rm --cached"

# Find the remote to the current repo
alias gr="git remote"
# Unstage a staged change `$ unstage <filename>`
alias unstage="git reset HEAD"
alias uncommit="git reset --soft HEAD~1"
# Discard a change `$ discard filename`
alias discard="git checkout --"
```

### Other

```bash
alias server="python -m SimpleHTTPServer 8000" # Creates a simple python server locally
alias nuke="rm -rf" # Remove files recursively and forcefully — use with caution!

# Run common NPM scripts
alias npm-p="npm run production"
alias npm-d="npm run development"

# Remove node_modules/ & package.json for doing a fresh npm install
alias rm_npm="rm -rf package-lock.json && rm -rf node_modules && echo 'Deleted package-lock.json & node_modules/'"
```

-----

[Back to main README](./README.md)
