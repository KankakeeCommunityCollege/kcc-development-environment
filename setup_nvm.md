# Setup & Use NVM

Now that nvm is working and you [verified your NVM installation](./installing_nvm.md#verify-installation), Nodejs needs to be installed.

## Install Nodejs

Install the current stable version using:

```bash
nvm install stable
```



## Install a Specific Version of Nodejs

```bash
nvm install v8.9.4
# or
nvm install 8.9.4 # no preceding "v" is valid too.
```



##  The `.nvmrc` File

Each project should contain an `.nvmrc` file to control which version of Nodejs it uses. Below is the entire contents of an example `.nvmrc` file.

```bash
v12.13.0
```



## Old Projects

Some old projects may have been developed using different versions of Nodejs. The following is a list of all Nodejs versions used in projects:

```bash
v8.9.4
v10.15.3
v12.13.0
```



## Upgrading Nodejs Versions

**Since the `gulp-cli` is dependent upon Nodejs, it is bound to the version it was installed with.** This can be demonstrated using the following commands in terminal:

```bash
nvm use 8.9.4
# Now using node v8.9.4 (npm v6.1.0)
which gulp
# /Users/wdzajicek/.nvm/versions/node/v8.9.4/bin/gulp

nvm use 12.13.0
# Now using node v12.13.0 (npm v6.13.0)
which gulp
# /Users/wdzajicek/.nvm/versions/node/v12.13.0/bin/gulp
```

If a new stable release of Nodejs comes out, remember to install the `gulp-cli` for that version:

```bash
npm install gulp-cli -g
```

## Errors After Nodejs Version Upgrade

After upgrading the Nodejs version used in a project you need run `npm i` . **Upgrading Nodejs will break the node-sass bindings**, and you will likely see errors returned at terminal when running `npm run production`. To resolve this rebuild them using `npm rebuild node-sass`.

## Add Function to Look for `.nvmrc` File

Our projects use an  `.nvmrc` file to control the version of Nodejs it uses.  When changing directories/projects, NVM does not look for the `.nvmrc` file itself--it needs a function to do that.

Add the following function to your bash initialization files to automatically switch Nodejs versions if a local `.nvmrc` file is present when using the `cd` command.

Preferably this would be in a  `~/.functions` file that gets called when you open a bash instance.

```bash
## Use a local .nvmrc file if present # from https://stackoverflow.com/a/48322289
enter_directory() {
  if [[ $PWD == $PREV_PWD ]]; then
    return
  fi

  PREV_PWD=$PWD
  [[ -f ".nvmrc" ]] && nvm use > /dev/null 2>&1 && nvm use | cowsay $n # Requires cowsay ## brew install cowsay
}

export PROMPT_COMMAND=enter_directory
```

**If you didn't [install cowsay](./install_rvm.md#install-cowsay-via-homebrew) either install it now `brew install cowsay` or use the following `enter_directory()` function instead:**

```bash
###############################
##  The no `cowsay` version  ##
###############################

## Use a local .nvmrc file if present # from https://stackoverflow.com/a/48322289
enter_directory() {
  if [[ $PWD == $PREV_PWD ]]; then
    return
  fi

  PREV_PWD=$PWD
  [[ -f ".nvmrc" ]] && nvm use
}

export PROMPT_COMMAND=enter_directory
```



## NPM & NPX

`npm` and `npx` are part of Nodejs and get installed with it.

### Upgrading the NPM Version

New releases of `npm` will come out. To update `npm` use the following command in terminal:

```bash
npm i npm -g
# Yes, you use npm to upgrade npm
```
