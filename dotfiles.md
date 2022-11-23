# Setting Up Dotfiles

We use `bash` to run our commands. Bash uses certain initialization files (dotfiles,) found in your users root folder (`~/`,) which can be customized.

Dotfiles are hidden files whose filename starts with a dot and has no file extension.

This document covers setting up dotfiles for `bash` and adding some helpful functions and aliases.

## Load Custom Dotfiles in `.bash_profile`

You should keep your bash functions and aliases separate.

To use custom `.aliases` and `.functions` files you need to load them in your `.bash_profile`.

Add the following to your `.bash_profile`:

```shell
# ~/.bash_profile

for file in ~/.{bash_prompt,aliases,functions}; do
        [ -r "$file" ] && [ -f "$file" ] && source "$file";
done;
unset file;

```
