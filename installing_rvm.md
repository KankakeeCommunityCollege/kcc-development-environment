# Ruby Version Manager (RVM)

>RVM is a command-line tool which allows you to easily install, manage, and work with multiple ruby environments from interpreters to sets of gems.

Official documentation found at <https://rvm.io/>.

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

### Install `cowsay` via Homebrew

```bash
brew install cowsay
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

### Fix RVM Path Warning

If you used the normal installation instructions (provided at https://rvm.io) you will most likely have path issues when running RVM:
```bash
rvm list

# Returned message:
Warning! PATH is not properly set up, '/home/<username>/.rvm/gems/ruby-2.6.3/bin' is not at first place,
         usually this is caused by shell initialization files - check them for 'PATH=...' entries,
         it might also help to re-add RVM to your dotfiles: 'rvm get stable --auto-dotfiles',
         to fix temporarily in this shell session run: 'rvm use ruby-2.6.3'.
```

This is because the RVM install script is slopy when it modifies your dotfiles. It looks for any kind of shell initiallization file (whether for `bash`, `zsh`, `fish`, etc.) and injects its path entry.

Your best option to fix this is to go through all the doftiles that the script just vomited code into and remove all RVM entries. Then, add them ONLY to the shell initialization files you use. Below is a list of all the files the RVM install script messes up:

- ~/.mkshrc
- ~/.profile
- ~/.bashrc 
- ~/.bash_profile 

Since I call most of my bash initiallization files from within `~/.bash_profile`, this is where I placed my only RVM entries.

My RVM path entry (`export PATH="$PATH:$HOME/.rvm/bin"`) is the last item in my `.bash_profile` to ensure that it is the last `PATH="...`  entry:

```bash
# ~/.bash_profile

[[ -s "$HOME/.profile" ]] && source "$HOME/.profile" # Load the default .profile

source ~/.bashrc # For NVM

for file in ~/.{bash_prompt,aliases,functions}; do
        [ -r "$file" ] && [ -f "$file" ] && source "$file";
done;
unset file;

[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm" # Load RVM into a shell session *as a function*

# Add RVM to PATH for scripting. Make sure this is the last PATH variable change.
export PATH="$PATH:$HOME/.rvm/bin"
```



---

[Back to main README](./README.md)