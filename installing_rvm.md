# Ruby Version Manager (RVM)

>RVM is a command-line tool which allows you to easily install, manage, and work with multiple ruby environments from interpreters to sets of gems.

We use RVM to ensure that we are using the same ruby environment across all the machines we develop on.

## RVM Prerequisites

On Mac OS X you will need gpg2 in order to install RVM's GPG keys. The easiest way to do this is use brew.

### Homebrew installation:

Install Homebrew using the following command in Terminal:

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Install GPG via Homebrew

Installing the `gnupg` Homebrew will install the `gpg` CLI.

```bash
brew install gnupg
```

## Installing RVM

## Get the GPG Keys

Before you install RVM, you need to get the GPG keys. Run the following command (using your [recently installed GPG command](#rvm-prerequisites)).

```bash
gpg --keyserver hkp://pool.sks-keyservers.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
```

## Run the Install Script

To run the RVM installation script, paste, and run, the following command into your terminal:

```bash
\curl -sSL https://get.rvm.io | bash -s stable
```
