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
- **[Mac OS X Prerequisites](./macosx_prerequisites.md)**
  - [Mac OS X Version](./macosx_prerequisites.md#mac-os-x-version)
  - [Xcode](./macosx_prerequisites.md#xcode)
  - [Install Xcode Command Line Tools](./macosx_prerequisites.md#install-xcode-command-line-tools)
- ~~[Windows Prerequisites](./windows_prerequisites.md)~~
- ~~[Linux Prerequisites](./linux_prerequisites.md)~~

-----

## Version Management

We use RVM and NVM to manage versions of Ruby and Node (respectively.)

<!-- no toc -->
- **[Ruby Version Manager (RVM)](./installing_rvm.md)**
  - [RVM Prerequisites](./installing_rvm.md#rvm-prerequisites)
    - [Install Homebrew](./installing_rvm.md#install-homebrew)
    - [Install GPG via Homebrew](./installing_rvm.md#install-gpg-via-homebrew)
  - [Installing RVM](./installing_rvm.md#installing-rvm)
    - [Get the GPG Keys](./installing_rvm.md#get-the-gpg-keys)
    - [Run the Install Script](./installing_rvm.md#run-the-install-script)
  - [Install `ruby-2.6.3`](./installing_rvm.md#install-ruby-263)
  - [Set the Default ruby version](./installing_rvm.md#set-the-default-ruby-version)
- **[Node Version Manager (NVM)](./installing_nvm.md)**
  - [NVM install script](./installing_nvm.md#nvm-install-script)
    - [Verify Installation](./installing_nvm.md#verify-installation)
  - [Add Bash Function](./installing_nvm.md#add-bash-function)
    - [Install `cowsay` via Homebrew](./installing_nvm.md#install-cowsay-via-homebrew)

-----

## Installing & Building a Project

<!-- no toc -->
- **[Installing and Building a Project](./installing_project.md)**
  - [Clone the Project](./installing_project.md#clone-the-project)
  - [Install Dependencies](./installing_project.md#install-dependencies)
  - [Running a Build](./installing_project.md#running-a-build)
    - [Production Build](./installing_project.md#production-build)
    - [Development Build](./installing_project.md#development-build)
  - [Update Browserslist `caniuse` Database](./installing_project.md#update-browserslist-caniuse-database)

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

## ~~Setting Up & Using RVM & NVM~~

- ~~[Setup RVM](./setup_rvm.md)~~
- ~~[Updating Ruby Versions](./update_ruby.md)~~
- ~~[Setup NVM](./setup_nvm.md)~~
- ~~[Updating Nodejs & npm Versions](./update_node.md)~~

-----

~~## Install Jekyll~~

- ~~[Install Jekyll](./installing_jekyll.md)~~
- ~~[Install the `kcc-gem-theme`](./installing_theme.md)~~

-----

