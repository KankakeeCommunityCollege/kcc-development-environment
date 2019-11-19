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

## The `.ruby-version` File

> ```bash
> rbenv: version `2.6.3' is not installed (set by viable-wombat.cloudvent.net/.ruby-version)
> Please use one of the following versions:
> 2.3.8
> 2.4.6
> 2.5.5
> 2.6.2
> ```

**Adding a `.ruby-version` file for a version that CloudCannon does not have/support will break the CloudCannon build**

CloudCannon **_only_** supports the following Ruby Versions:

- 2.3.8
- 2.4.6
- 2.5.5
- 2.6.2
