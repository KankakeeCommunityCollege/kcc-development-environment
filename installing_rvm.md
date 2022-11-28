# Ruby Version Manager (RVM)

> *Last updated on **11/22/2022***
>
>RVM is a command-line tool which allows you to easily install, manage, and work with multiple ruby environments from interpreters to sets of gems.

| Current Ruby Version (for KCC projects) |
|-----------------------------------------|
| `ruby-2.6.3`                            |

- [Ruby Version Manager (RVM)](#ruby-version-manager-rvm)
  - [RVM Prerequisites](#rvm-prerequisites)
    - [Install Homebrew](#install-homebrew)
    - [Install GPG via Homebrew](#install-gpg-via-homebrew)
  - [Installing RVM](#installing-rvm)
    - [Get the GPG Keys](#get-the-gpg-keys)
    - [Run the Install Script](#run-the-install-script)
  - [Install `ruby-2.6.3`](#install-ruby-263)
  - [Set the Default ruby version](#set-the-default-ruby-version)

Official documentation found at <https://rvm.io/>.

---

## RVM Prerequisites

On Mac OS X you will need gpg in order to install RVM's GPG keys. The easiest way to do this is install `gnupg` via **Homebrew**.

### Install Homebrew

Install Homebrew using the following command in terminal:

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Install GPG via Homebrew

Installing the `gnupg` Homebrew package will install the `gpg` CLI (needed to install RVM.)

```bash
brew install gnupg
```

## Installing RVM

Now that the prerequisites for RVM are installed, you can proceed with installing the GPG keys and running the installation script.

### Get the GPG Keys

Before you install RVM, you need to get the GPG keys. Run the following command (using your [recently installed GPG command](#rvm-prerequisites)).

```bash
gpg --keyserver hkp://pool.sks-keyservers.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
```

### Run the Install Script

To run the RVM installation script, paste, and run, the following command into your terminal.

RVM recommends running the installation script using the escaped `\curl` command to prevent it from "misbehaving".

```bash
\curl -sSL https://get.rvm.io | bash -s stable
```

## Install `ruby-2.6.3`

To install `ruby-2.6.3` use the following rvm command:

```bash
rvm install 2.6.3
```

## Set the Default ruby version

To set the default ruby version:
```bash
rvm --default use 2.6.3
```

-----

[Back to main README](./)
