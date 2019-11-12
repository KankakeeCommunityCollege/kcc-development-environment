# Ruby Version Manager (RVM)

>RVM is a command-line tool which allows you to easily install, manage, and work with multiple ruby environments from interpreters to sets of gems.

We use RVM to ensure that we are using the same ruby environment across all the machines we develop on, for a given project.

---

## RVM Prerequisites

On Mac OS X you will need gpg in order to install RVM's GPG keys. The easiest way to do this is install `gnupg` via homebrew.

### Homebrew installation:

Install Homebrew using the following command in terminal:

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Install GPG via Homebrew

Installing the `gnupg` Homebrew will install the `gpg` CLI.

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

To run the RVM installation script, paste, and run, the following command into your terminal. Escaping `curl` with a `\` ensures that `curl` will run without using any aliases. RVM recommends running the installation script using the escaped `\curl` command to prevent it from "misbehaving".

```bash
\curl -sSL https://get.rvm.io | bash -s stable
```

---

[Back to main README](./README.md)
