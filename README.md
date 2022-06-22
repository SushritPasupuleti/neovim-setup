# Neovim Experiments
A repo that I'm using to learn vim/neovim.

> Just formatted this `README` and added this line via `neovim`. Massive flex :O

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

