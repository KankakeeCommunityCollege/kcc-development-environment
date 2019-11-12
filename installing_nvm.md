# Node Version Manager (NVM)

> Node Version Manager - POSIX-compliant bash script to manage multiple active node.js versions

Official documentation found at <https://github.com/nvm-sh/nvm>.

---

## NVM install script

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash
```

## Verify Installation

You should completely exit all terminal instances and quit whichever terminal program or app you are using. Restart your preferred terminal and run the following command:

```bash
command -v nvm

## If working properly it will return the following:
nvm
```

If you don't see `nvm` returned from running `command -v nvm`, and didn't see any issues when running the installation script, the export configuration RVM adds to your dotfiles is most likely in the wrong place.

You will need to go through your bash initialization files and make sure the following lines of code are getting called when you startup your terminal emulator app/program.


```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

Ideally you have an `~/.exports` dotfile for all of your `export`'s that is called from one of your bash-initialization files.

---

[Back to main README](./README.md)
