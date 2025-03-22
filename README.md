# wppfzf ![](https://img.shields.io/badge/version-0.1.0-green.svg) [![](https://img.shields.io/badge/license-GPLv3-orange.svg)](https://github.com/channel-42/wppfzf/blob/master/LICENSE) 
<p align="center"><i>Browse and download images from reddit with fzf and ueberzug</i></p>
<p align="center"><img src="https://github.com/botus99/wppfzf/blob/master/resources/demo.gif" align="center" alt="demo gif"title="fancy demo"></p>

# Content

1. [Installation](#installation)
2. [Usage](#usage)
3. [Theming](#theming)
4. [Notes](#notes)


# Installation

### Arch

This fork is not in the AUR.

To install the original wppfzf AUR package, use your AUR-helper of choice. For example:
```bash
paru -S wppfzf
```

### General
**Dependencies**
- bash
- fzf
- ueberzug

Install the necessary dependencies first. Then, get the **latest release** by running:

```bash
sudo wget "https://raw.githubusercontent.com/botus99/wppfzf/master/wppfzf" \
-O /usr/bin/wppfzf
sudo chmod +x /usr/bin/wppfzf
```

# Usage

### All cli options are shown and explained when running `wppfzf -h` 

To start a simple query, run `wppfzf` with no arguments. This will use the defaults. Each line shows the posts title as well as the number of up- and downvotes. 

- To open the currently selected image in your default image-viewer, press `ctrl-p`.
- To download the currently selected image, press `ENTER`. 
- Press `ESC` to quit wppfzf.

To search a specific subreddit, use the `-r` option, `-l N` will limit the api query to N posts. 

> Note that less images may be show in wppfzf itself due to filtering of incompatible posts (e.g. imgur albums).

wppfzf defaults to searching the last 100 posts of *r/wallpaper* & *r/wallpapers* and saving desired images to `$HOME/.wallpapers/reddit`. These settings, as well as the default preview window size and location, can be temporarily changed through the cli arguments. 

To make these changes permanent, the script itself has to be edited. The settings are located at the top of the script: 

```bash
# query limit 
LIMIT=100
# default subreddit to search
SUBREDDIT="wallpaper+wallpapers"
# dir to save images to
declare -x WPP_FZF_DL_DIR=$HOME/.wallpapers/reddit
# default preview position
declare -x DEFAULT_PREVIEW_POSITION="up"
# default preview size
declare -x DEFAULT_PREVIEW_SIZE="67%"
```

# Theming

Theming the fzf interface is done at the top of the script itself. To see all available color options, refer to fzf's man page.

```bash
# default interface colors: 'option:term_color_code'
COLOR_OPTS="bg+:0,fg:15,fg+:1,border:8,hl+:2,prompt:15,hl:2,pointer:8,info:8,spinner:1"
```

# Notes

This project is made possible through both [fzf](https://github.com/junegunn/fzf) and [ueberzug](https://github.com/seebye/ueberzug).
