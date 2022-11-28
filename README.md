# KCC Development Environment

> *Last updated on **11/28/2022***
>
> Documentation on setting up the development environment needed for KCC's redesign projects.

-----

## Overview

Our projects use **Ruby** and **Node.js** to build static HTML sites, and compile assets. The documents in this repo will guide you through setting up the development environment currently used by KCC.

-----

## Prerequisites

<!-- no toc -->
- **[Mac OS X Prerequisites](./prerequisites/)**
  - [Mac OS X Version](./prerequisites/#mac-os-x-version)
  - [Xcode](./prerequisites/#xcode)
  - [Install Xcode Command Line Tools](./prerequisites/#install-xcode-command-line-tools)
- ~~[Windows Prerequisites](./prerequisites/windows_prerequisites.md)~~
- ~~[Linux Prerequisites](./prerequisites/linux_prerequisites.md)~~

-----

## Version Management

We use RVM and NVM to manage versions of Ruby and Node (respectively.)

<!-- no toc -->
- **[Ruby Version Manager (RVM)](./rvm/)**
  - [RVM Prerequisites](./rvm/#rvm-prerequisites)
    - [Install Homebrew](./rvm/#install-homebrew)
    - [Install GPG via Homebrew](./rvm/#install-gpg-via-homebrew)
  - [Installing RVM](./rvm/#installing-rvm)
    - [Get the GPG Keys](./rvm/#get-the-gpg-keys)
    - [Run the Install Script](./rvm/#run-the-install-script)
  - [Install `ruby-2.6.3`](./rvm/#install-ruby-263)
  - [Set the Default ruby version](./rvm/#set-the-default-ruby-version)

<br>

- **[Node Version Manager (NVM)](./nvm/)**
  - [NVM install script](./nvm/#nvm-install-script)
    - [Verify Installation](./nvm/#verify-installation)
  - [Add Bash Function](./nvm/#add-bash-function)
    - [Install `cowsay` via Homebrew](./nvm/#install-cowsay-via-homebrew)

-----

## Installing & Building a Project

<!-- no toc -->
- **[Installing and Building a Project](./projects/)**
  - [Clone the Project](./projects/#clone-the-project)
  - [Install Dependencies](./projects/#install-dependencies)
  - [Running a Build](./projects/#running-a-build)
    - [Production Build](./projects/#production-build)
    - [Development Build](./projects/#development-build)
  - [Update Browserslist `caniuse` Database](./projects/#update-browserslist-caniuse-database)

-----

## Setting Up Dotfiles

<!-- no toc -->
- [Setting up Dotfiles](./dotfiles/)
  - [Load Custom Dotfiles in `.bash_profile`](./dotfiles/#load-custom-dotfiles-in-bash_profile)
  - [`.functions`](./dotfiles/#functions)
  - [`.aliases`](./dotfiles/#aliases)
    - [Folder Navigation](./dotfiles/#folder-navigation)
    - [Git](./dotfiles/#git)
    - [Other](./dotfiles/#other)


-----

## Publishing Branch Workflow

- [Publishing Branch Workflow](./publishing/)

-----

## Archived Content

Archived content is documentation that is either outdated or no longer relevant.

### ~~Setting Up & Using RVM & NVM~~

- ~~[Setup RVM](./archive/setup_rvm.md)~~
- ~~[Updating Ruby Versions](./archive/update_ruby.md)~~
- ~~[Setup NVM](./archive/setup_nvm.md)~~
- ~~[Updating Nodejs & npm Versions](./archive/update_node.md)~~

### ~~Install Jekyll~~

- ~~[Install Jekyll](./archive/installing_jekyll.md)~~
- ~~[Install the `kcc-gem-theme`](./archive/installing_theme.md)~~

-----

