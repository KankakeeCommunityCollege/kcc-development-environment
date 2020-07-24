# Configure `kcc-gem-theme` in Your Project

## Gemfile

To use the `kcc-gem-theme` just installed in [Installing the `kcc-gem-theme` in a Project](./installing-gem-theme.md) you also need to add it to your project' `Gemfile`:

```shell
source 'https://rubygems.org'

gem 'jekyll', '~> 4.0.0'
gem 'kcc-gem-theme', '~> 1'
```

**_IMPORTANT:_ Be sure to use the tilde (~) greater-than version specifier _and only specifiy a MAJOR version number!_**

This is the best practice for our adherence to semantic versioning 2.0.0 (See <https://semver.org/>). The expresion `'~> 1'` ensure's it will download the latest version of 1.X.X but nothing above version 1. It could also be represented as `'>= 1'` and `'< 2'`.

This really benefits us when it comes to releasing a new MAJOR version i.e. `2.0.0`. By SemVer definition, when a MAJOR version is released, Old code (i.e. version 1.0.0 code) may break with the update. This way, when we release version 2 the CloudCannon sites cannot update to it (which could cause every project to break when a new build is triggered in CC.

_**Note:** Jekyll is required to install the `kcc-gem-theme`._

## Jekyll `_config.yml`

You also need to add the following key-value pair to the Jekyll configuration file (usually `./_config.yml`):

```yaml
theme: "kcc-gem-theme"
```



