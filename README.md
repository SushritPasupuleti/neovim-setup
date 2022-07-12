# Neovim Setup

A repo that I'm using to learn vim/neovim.

> Just formatted this `README` and added this line via `neovim`. Massive flex :O

You can find my 2 configs in [coc version](./coc-init.vim) and [lsp version](./lsp-init.vim)

## Some basic Navigation

> Press `i` to enter `insert mode`.

> Press `escape` to exit current mode.

This lets you actually make changes to your files. Until then it's all read-only. Good to read through some code without worrying about accidental changes.

Creating and opening files:

```bash
# while in the directory you want to work in
nvim nameoffile.extension
```

Creates or opens the file specified depending on it's existence on disk.

Opening entire director:

```bash
nvim .
```

Opens and displays a file browser that you can naviagate through. Press `enter` to open file. Neat out-of-the-box feature.

## Editting the Config

While in your default working directory. Create/Access the `.config` folder. This usually already exists so beware.

```bash
mkdir .config
cd .config/
```

Make a `nvim` directory:

```bash
mkdir nvim
```

Create neovim config file:

```
nvim init.vim
```

### Sample Config

My current config will be added to this repo

```vim
:set number
:set relativenumber
:set autoindent
:set tabstop=4
:set shiftwidth=4
:set smarttab
:set softtabstop=4
:set mouse=a
```

## Install a Plug-in Manager

I am using [vim-plug](https://github.com/junegunn/vim-plug) for this. Follow install instructions from there.

Setting up `vim-plug` requires adding the following to the `init.vim` file:

```.vim
call plug#begin()
" all your plugins...
Plug 'url to your plugin'
call plug#end()
```

Also install `exuberant ctags`

```bash
brew install ctags
```

Installing the Plugins (One time only)

Inside your nvim instance run the following in command mode:

```vim
:PlugInstall
```

Your plugins are now installed!

Deleting plugins:

> Remove the `Plug ''` entry from the `init.vim` file.

> Run `:PlugClean`.

## Install coc

For autocompletions.

After adding the Plug config:

```.vim
Plugin 'neoclide/coc.nvim'
```

Go to your `plugged` folder.

On Mac: `~/.local/share/nvim/plugged`.

On Linux: `~/.config/nvim/plugged`.

```bash
cd coc.vim/
yarn
```

This installs all dependencies. Takes a while.

### Installing Language Servers

Install using:
> :CocInstall name-of-lsp

- Python: `coc-pyright`.

- JSON: `coc-json`.

- Markdown: `coc-markdownlint`.

- JS/TS: `coc-tsserver`.

- HTML: `coc-html`.

- Java: `coc-java`.

- CSS: `coc-css`.

- Dart: `coc-flutter`.

- Bash: `coc-sh`.

- prettier: `coc-prettier`.

## Integrity Check

> :checkhealth

## Useful keyboard shortcuts

### Undo/Redo

Use `:u` and `:r` respectively.

### Search and Highlight

In `command` mode. Press <kbd>/</kbd> to enter search. Now type a regex pattern you would like to search.

Clear the selections by using `:noh`.

### Copy/Paste/Select

To select any text, you must enter `visual` mode. Press <kbd>v</kbd> in `normal` mode for this.

- Use arrow keys to expand the selection.

- <kbd>d</kbd> Deletes the selection.

- <kbd>y</kbd> "yank"/copy the selection.

- <kbd>p</kbd> Paste the selection.

- Search by using these 4 in conjuntion on the selected text: <kbd>y</kbd> <kbd>q</kbd> <kbd>/</kbd> <kbd>p</kbd>

- <kbd>r</kbd> Replace selection with text you will now type.

#### Copy/Paste Across Terminals

Use: <kbd>"</kbd> <kbd>+ </kbd> <kbd> y</kbd> and <kbd>"</kbd> <kbd>+ </kbd> <kbd> p</kbd> from `visual` mode.

### For Tiling

- <kbd>Ctrl</kbd> <kbd>W</kbd> <kbd>S</kbd> (upper case) for horizontal splitting

- <kbd>Ctrl</kbd> <kbd>W</kbd> <kbd>v</kbd> (lower case) for vertical splitting

- <kbd>Ctrl</kbd> <kbd>W</kbd> <kbd>Q</kbd> to close one

- <kbd>Ctrl</kbd> <kbd>W</kbd> <kbd>C</kbd>trl+W to switch between windows

- <kbd>Ctrl</kbd> <kbd>W</kbd> <kbd>J</kbd> (<kbd>x</kbd> or <kbd>K</kbd>, <kbd>H</kbd>, <kbd>L</kbd>) to switch to adjacent window (intuitively up, down, left, right)

## Loading Lua Scripts

- Create a `lua` directory under `.config/nvim/`. 

- Create another subdirectory under `lua`. Use your name for example.

- Write all your scripts here. Ex: `options.lua`.

- At the `nvim/lua` directory level create a `config.lua` and inside that add references to all subdirectory contained lua scripts with:

```lua
require "example_subdir.option"
```

In your `init.vim` load the script with:

```vim
lua require('config')
```

## LSP Instead of coc

After tinkering with coc, which is easier to get started with, I realized I need greater granular control over my configs while also keeping them light weight. So I'm switching to the native LSP.

Add the `nvim-lspconfig` plugin.

```vim
Plug 'neovim/nvim-lspconfig'
```

### Installing LSPs

- Python: `yarn global add pyright`

- JS/TS: `yarn global add typescript typescript-language-server`

## Installing Glow for Markdown Preview

```bash
# macOS or Linux
brew install glow

# macOS (with MacPorts)
sudo port install glow

# Arch Linux (btw)
pacman -S glow

# Void Linux
xbps-install -S glow

# Nix
nix-env -iA nixpkgs.glow

# FreeBSD
pkg install glow

# Solus
eopkg install glow

# Windows (with Scoop)
scoop install glow

# Android (with termux)
pkg install glow
```

```vim
Plug 'ellisonleao/glow.nvim', {'branch': 'main'}
```

## Telescope

You need `ripgrep` for `live_grep`.

```bash
brew install ripgrep
```

## JSONQ

```bash
brew install jq
```

## Go Setup

Install `gopls` after adding `gopls` to your LSPConfig.

```bash
brew install gopls
```

## Global Find and Replace

```bash
brew install ripgrep
brew install gnu-sed
```