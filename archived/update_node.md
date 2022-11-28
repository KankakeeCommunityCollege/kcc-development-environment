# Updating Nodejs & npm Versions for Projects

> When using `nvm`, global `npm` installs, node-sass bindings, & npm installs are bound to the version of Nodejs/npm used upon installation.

## Updating Nodejs Versions

When a new stable version of Node.js comes out, you should install it and update the repositories. To check for new versions, either go to [nodejs.org](https://nodejs.org/en/) (LTS recommended for most users) or run `nvm ls-remote` and find the latest stable release `(Latest LTS: <VERSION_NAME>)`.

To download a new version of Nodejs, you can either run `nvm install <VERSION_NUMBER>` where `<NODE_VERSION>` is the specific SemVer # (e.g. `12.13.1`) or run `nvm install --lts`

### Make Sure You are Using the New Nodejs Version

**In the project you are updating run:**
```bash
nvm use
```

### Update `npm`

Sometimes when you download the latest LTS of Nodejs, it comes with a slightly outdated version of `npm`. After updating Nodejs versions you should just update `npm` right away:
```bash
npm i npm -g  ## Yes, npm gets updated via npm.
```

### Update the `.nvmrc` File

Be sure to update the version the `.nvmrc` file to reflect the new version number. The version number should be the only contents in the `.nvmrc` file:
```
12.13.1
```

This way, every-time you `cd` into the project, the `enter_directory()` function (see [Add Function to Look for `.nvmrc` File](./setup_nvm.md#add-function-to-look-for-nvmrc-file)) will switch to the correct version for that project automatically.

### Install `gulp-cli`

Since you just installed a new version of Nodejs/npm your bindings to Gulpjs are broken. **You must reinstall `gulp-cli`.**

To reinstall `gulp-cli` run the following command in terminal:
```bash
npm i gulp-cli -g
```

### Update `node_modules`

You should run `npm i` again after updating Nodejs/npm versions in a project.


### Test the Projects Build

Run the production build command to ensure nothing is broken:
```
npm run production ## or `npm-p` if you have the alias.
```

### Fix `node-sass` Bindings

After updating Nodejs/npm and running an `npm` install, the normal build commands (`npm run production`) will break, throwing a `node-sass` errors. If this happens simply run the following command in the project:
```bash
npm rebuild node-sass
```
