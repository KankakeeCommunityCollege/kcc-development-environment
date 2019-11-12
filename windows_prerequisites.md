# Windows Prerequisites

> Get your Windows machine ready for setting up the development environment.

This documentation assumes you are using an up-to-date Windows 10 machine with relatively modern hardware.  Running webpack and gulp/jekyll in parallel may cause performance issues on less capable machines.

## Overview

To have a more similar environment to macOSX or Linux, this document walks you through setting up the "Windows Subsystem for Linux" & installing Ubuntu to be able to run commands like `bash` at a Windows `cmd.exe` instance.

On Jekyll's [Windows installation page](https://jekyllrb.com/docs/installation/windows/) it says:

> The easiest way to run Jekyll is by using the RubyInstaller for Windows.

**This may be true, _however, our development environment uses more than Jekyll running on ruby._**

## Enable the Linux Subsystem

> Before installing any Linux distros for WSL, you must ensure that the "Windows Subsystem for Linux" optional feature is enabled

1. Open PowerShell as Administrator and run:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

2. Restart your computer when prompted.

## Install Ubuntu

The easiest way to run Ubuntu commands on the Linux subsystem in Windows is through the Microsoft Store.

1. Open the Microsoft Store app & search for "Ubuntu".
2. Find and install Ubuntu (by Canonical) with the "Get" button.

To check your Ubuntu installation open `cmd.exe` with Administrator privileges and run:

```bash
bash
```

Make sure your dependencies are up to date (passing the `-y` flag is saying "yes" to the `y/n` prompt before it installs):

```bash
sudo apt-get update -y && sudo apt-get upgrade -y
```

## Install git-scm

Download git-scm from <https://git-scm.com/>. Install with all the default settings.

---

[Back to main README](./README.md)
