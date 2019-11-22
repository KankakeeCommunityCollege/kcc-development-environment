# Updating Ruby Versions

> When using RVM, Gems, including Jekyll, are bound to the version used upon installation

## Check for New Versions

Run the following RVM command to check for new releases:
```bash
rvm list known
# Returns a long list shown below. The first entries are what we want--"MRI Rubies":
# MRI Rubies
[ruby-]1.8.6[-p420]
[ruby-]1.8.7[-head] # security released on head
[ruby-]1.9.1[-p431]
[ruby-]1.9.2[-p330]
[ruby-]1.9.3[-p551]
[ruby-]2.0.0[-p648]
[ruby-]2.1[.10]
[ruby-]2.2[.10]
[ruby-]2.3[.8]
[ruby-]2.4[.6]
[ruby-]2.5[.5]
[ruby-]2.6[.3]
[ruby-]2.7[.0-preview1]
ruby-head
```

In the above list, `ruby-2.6.3` is the latest stable (`[ruby-]2.7[.0-preview1]` is a preview release).

## Install the Latest Version

From the prior step, we know that `ruby-2.6.3` is latest. To install it run:
```bash
rvm install 2.6.3
```

## Update the `.ruby-version` File

Be sure to update the `.ruby-version` file for the projects after updating versions. You should update the `.ruby-version` file right away to make sure you are always using the correct version for that project.

The entire contents of a `.ruby-version` file should be only a SemVer version #:
```
2.6.3
```

## Switch to Latest Version

> **Make sure you are using the proper ruby-version prior to installing gems or running `bundle install` in a project.**

After `cd`ing into a project you want to update, ensure you are using the correct version of ruby.

If you already updated the `.ruby-version` file you can simply run `rvm use`.
Otherwise, run the following command (assuming `ruby-2.6.3` is the version you just updated on your system to):
```bash
rvm use 2.6.3
```

## Reinstall Jekyll & Bundler

Since Gems are bound to the ruby-version they were installed with, you have to reinstall them when updating versions. Run the install commands again for Jekyll & Bundler:
```bash
gem install jekyll bundler
```

## Run `bundle install` in Projects

A project's gems are also bound to the ruby-version they were installed with. You should run a bundle install in the projects after switching ruby-versions:
```bash
bundle i
```
