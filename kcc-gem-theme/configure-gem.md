# Configure `kcc-gem-theme` in Your Project

## Gemfile

To use the `kcc-gem-theme` just installed in [Installing the `kcc-gem-theme` in a Project](./installing-gem-theme.md) you also need to add it to your project' `Gemfile`:

```shell
source 'https://rubygems.org'

gem 'jekyll', '~> 4.0.0'
gem 'kcc-gem-theme', '~> 1'
```

_**Note:** Jekyll is required to install the `kcc-gem-theme`._

## Jekyll `_config.yml`

You also need to add the following key-value pair to the Jekyll configuration file (usually `./_config.yml`):

```yaml
theme: "kcc-gem-theme"
```



