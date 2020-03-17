# Setup the Same Development Environment on macOs Catalina

## Remove the `bash` Deprecation Warning

In macOS Catalina, the default shell was switched to Zsh.
Upon opening a terminal or terminal emulator window, you will see this deprecation warning:

```bash
The default interactive shell is now zsh.
To update your account to use zsh, please run `chsh -s /bin/zsh`.
For more details, please visit https://support.apple.com/kb/HT208050.
```

To remove this deprecation warning, add the following line to you `.bash_profile` 
(create a `~/.bash_profile` file if you don't have one alread):

```
export BASH_SILENCE_DEPRECATION_WARNING=1 # Silence the new Catalina Bash warning
```

Change the default shell back to bash:

> I ❤️ bash 

```bash
chsh -s /bin/bash
```
