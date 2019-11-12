# Setup & Use RVM

> Jekyll requires Ruby > 2.4.0. As macOS Mojave 10.14 comes only with ruby 2.3.x, you’ll have to install a newer version of Ruby.

## Install Ruby

Now that RVM is installed we can use it to install our desired rubies. To install `ruby-2.5.0` run the following command in terminal:

```bash
rvm install 2.5.0
```

Most of the repos were developed in `ruby-2.5.0`. The projects are being updated to use the latest stable `ruby-2.6.3`. Since this is only a minor and patch version difference, there shouldn't be any breaking changes.

## Installing and Using a New Ruby Version

If a new stable release of ruby comes out, **be sure to reinstall the Bundler and Jekyll gems since they are ruby based**.

```bash
gem install bundler jekyll
```

**When using RVM, your Jekyll and Bundler installations are bound to the ruby version you were using when you installed them. Anytime you switch ruby versions in rvm (`rvm use 2.5.0`) you are also switching the associated Jekyll & Bundler Gem installations as demonstrated below.**

```bash
rvm use 2.5.0
# Using ~/.rvm/gems/ruby-2.5.0
which jekyll
# ~/.rvm/gems/ruby-2.5.0/bin/jekyll

rvm use 2.6.3
# Using /Users/wdzajicek/.rvm/gems/ruby-2.6.3
which jekyll
# /Users/wdzajicek/.rvm/gems/ruby-2.6.3/bin/jekyll
```

## Set the Default Ruby Version

To set the default ruby version for RVM use the following command:

```bash
rvm --default use 2.6.3
```



## Version Control Using `.ruby-version` File

> This file is also supported by [chruby](https://github.com/postmodern/chruby#readme) and [rbenv](https://github.com/sstephenson/rbenv#readme). `.ruby-version` is just a ruby name so it does not require trusting and is simpler to use than `.rvmrc`.

> `.rvmrc` has one major flaw - it requires trusting to prevent execution of unauthorized code, which makes it hard to use and complicates deployment to production

For simplicity, projects use a `.ruby-version` file to control the ruby environment for that project.  Below is an example `.ruby-version ` file--its only contents being a valid version number for ruby.

Example `.ruby-version` file:

```bash
2.3.6
```
