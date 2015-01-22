Dotfiles
========

This is collection of dotfiles (zsh/git/aliases/configs/etc) to setup my development environment.

Get the files:

    cd ~
    git clone git@github.com:stunpix/dotfiles.git .dotfiles

Initialize environment, with:

    ~/.dotfiles/dots on

and restart shell.

If you no longer want it:

    ~/.dotfiles/dots off

this will remove all links/files created by dot modules, then you can safely delete `.dotfiles` folder.

Writing dot modules
-------------------

To add new dot module, for example `bash`, create new folder `~/.dotfiles/bash` and add there `dotconf` file. This file is used to enable or disable module and executed each time you run `~/.dotfiles/dots`. Then add to `dotconf` following lines:

	# add enable/disable hooks
    enable_functions+=(enable_bash)
    disable_functions+=(disable_bash)

    enable_bash() {
    	# some initialization sequence (installing files, links, etc)
    }

    disable_bash() {
    	# some finalization sequence (removing files, links, etc)
    }

Folders that have no `dotconf` file are skipped.

zsh submodules
--------------

There is one convention about zsh submodules: they are also must be placed in `~/.dotfiles`, but must have `zsh-` prefix and have `zshrc` file inside. Once zsh shell starts, it includes all `~/.dotfiles/zsh-*/zshrc` files from main `~/.zshrc` file, so you can easely extend it by creating new `zsh-` prefixed folders with `zshrc` files inside.