# Installing Gulpjs

Official documentation found at <https://gulpjs.com/>.

Gulp requires both a global installation of the `gulp-cli` and local installation of `gulp` in your project.

## Install the gulp-cli

```bash
npm install gulp-cli -g
```

## Install Gulp in a Project

**When you run `sh install.sh`, `npm install` gets called. This will install gulp from the `package.json`'s `devDependencies`**

If you wanted to reinstall gulp in a project run the folowing command in terminal:

```bash
npm i gulp --save-dev
```

## Upgrading Nodejs

**Remember that if you install a new version of Nodejs and want to start using it in a project, you must install the `gulp-cli` once using the new Nodejs version.**

```bash
npm i gulp-cli -g
```
