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
