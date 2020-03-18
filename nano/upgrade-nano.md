# Upgrade GNU nano

> macOS comes pre-installed with nano-2.X which cannot do syntax highlighting and other newer plugins.

## The tl;dr

The tl;dr using `nano-4.8` as the version number:

1. Download the current gzipped source code (`nano-4.8.tar.gz`) from the [GNU nano Download](https://www.nano-editor.org/download.php) page and place it in your user root (`~/`).
2. Unzip it: `tar -zxvf ~/nano-4.8.tar.gz`
3. Go into the resulting dir: `cd ~/nano-4.8`
4. Configure make: `./configure`
5. Make: `make`
6. Make Install: `sudo make install`

Restart Terminal & test out the nano install - **Quit all terminal instances completely first**.  Test `nano` via running `nano test.md`. Nano should display its version number in the very top-left corner, while open (`GNU nano 4.8`).

## Download the source code

Go to the [Downloading GNU nano](https://www.nano-editor.org/download.php) page and download "The source code gzipped:" currently listed as `nano-4.8.tar.gz`.

Your filename and version may vary but follow the `nano-<#>.<#>.tar.gz` convention where `<#>` is a number representing the current version.

**Download the `*.tar.gz` file directly into your root (`~/`) directory**

## Unzip the Download

After downloading into your root directory (you should still be in `~/`), unzip the download using the following command:
```bash
cd ~/
tar -zxvf nano-4.8.tar.gz
```

## Configure `make`

Go into the directory created as a result of the `tar` command, used above:
```bash
cd nano-4.8
```

Configure `make` using:
```bash
./configure
```

## Run `make`

```bash
make
```

## Install `nano`

Install your new version of nano using `make install`. **Be sure to prepend the command using `sudo`**:
```bash
sudo make install
```

## Restart Terminal

I always do this after messing with something like a CLI install.
