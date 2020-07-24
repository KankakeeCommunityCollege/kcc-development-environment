# KCC Development Environment

> Documentation on setting up the development environment needed for KCC's redesign projects.

## Overview

Our projects use both Node.js & a Ruby environment to compile static HTML sites. The documents in this repo will guide you through setting up the development environment currently used by KCC.

## Platform

A nearly identical development environment can be achieved on Mac OS X, Linux, and Windows.  With minor alterations, you can use the same dotfiles cross-platform. The installation instructions vary slightly by platform.

## Prerequisites

- [Mac OS X Prerequisites](./macosx_prerequisites.md)
- [Windows Prerequisites](./windows_prerequisites.md)
- [Linux Prerequisites](./linux_prerequisites.md)

## Environment Version Management

- [Install Ruby Version Manager (RVM)](./installing_rvm.md)
- [Install Node Version Manager (NVM)](./installing_nvm.md)

## Setting Up & Using RVM & NVM

- [Setup RVM](./setup_rvm.md)
- [Updating Ruby Versions](./update_ruby.md)
- [Setup NVM](./setup_nvm.md)
- [Updating Nodejs & npm Versions](./update_node.md)

## Install Jekyll

- [Install Jekyll](./installing_jekyll.md)
- [Install the `kcc-gem-theme`](./installing_theme.md)

## Install Gulpjs

- [Install Gulp](./installing_gulp.md)

## KCC Gem Theme

- [KCC Gem Theme](https://github.com/KankakeeCommunityCollege/kcc-development-environment/tree/master/kcc-gem-theme#kcc-gem-theme)
  - [Accordion](./kcc-gem-theme/accordion.md)
  - [Google Translate](./kcc-gem-theme/translate.md)
  - [Hero Slider](./kcc-gem-theme/hero-slider.md)
  - [Global Nav](./kcc-gem-theme/global-nav.md)
  - [Making Changes to the Theme](./kcc-gem-theme/ruby-gems.md)

## Architecture Overview

## CloudCannon

- [CloudCannon](./cloudcannon/)
- [CloudCannon FTP Settings](./cloudcannon/cloudcannon-ftp.md)


## GNU nano

- [nano](./nano/)
- [Upgrade to latest](./nano/upgrade-nano.md)

## Vocabulary and Acronyms

### Acronyms

These acronym's may be used throught the markdown files in this repository. It is best to be familier with the acronym's and vocabulary, prior to diving in to all these informational markdown files. Please look up vocabulary that you don't know—a simple intenet search usually helps.

- CC = CloudCannon
- CMS = Content Manegement System
- CLI = Command Line Interface


### Vocab

- **Command Line Interface** - A command line program that accepts text input to execute operating system functions (adapted from www.w3schools.com)
- **Terminal, Terminal Emulator, Command Line, Command Prompt** - Emulators that create a command line instance e.g. Terminal (Mac's stock), CMD.exe (Win's basic stock), PowerShell, iTerm2, Terminator (Ubuntu), etc.
- **Bash, Shell Zsh/Zshell** - A shell is a linux based command-line interpreter that creates a command-line user interface. Bash and Zshell is a more advanced shell language. This is what your terminal emulator creates—a shell instance. Bash and Zsh are pretty standard unix shell languages available on Ubuntu and Mac (sometimes as default)
- **CloudCannon** - Our current cloud-based CMS (See Acronynms above)
- **Nodejs** - A JavaScript environment (much like your browser) and CLI (See above) that use the same V8 JavaScript runtime engine as browsers
- **Gulp & Gulpjs** - A JavaScript task runner that runs on Nodejs and uses CommonJS
- **ES ES6, ES2015** - ECMAScript is a JavaScript Standard to ensure cross-browser compatibility of websites. ES6 and 2015 versions of ECMAScript
**- MDN, JavaScript.info** - GREAT resources for all things JavaScript and ES. *NOTE* Not every JavaScript example you see on these sites will work in every browser—you better know what your doing when using ES2015 and ES6.