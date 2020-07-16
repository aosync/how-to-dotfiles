# How to dotfiles

I am going to explain a good method to manage dotfiles (best is arguable). I use the git bare repos method.  
A git bare repo is basically a git repo without a definite tree, and the contents of its `.git` lives in a folder that you decide yourself.
  
First, create the git repo where you want, it can be in `~` but it could be anywhere else if you like having your home uncluttered. I personally put it in `~/src` which is a folder that contains my repositories.

```sh
git init --bare ~/dots
```

This will create the bare repo, with what you'd usually expect to be in a `.git` in it.

Now create an git alias that will be used to address your dots repo with your `~` as the tree. For this, add something along the lines of

``` sh
alias dots="git --git-dir=$HOME/dots --work-tree=$HOME"
```

in your shellrc file.  
  
At this point, pretty much everything is ready, except that it's not easy to keep track of the files that you actually want shown in your dotfiles repo.  
For this, I use what I call a `trackfile` that I store in my config folder (`~/etc` for me) and I put everything that I want listed in it.  
Mine looks like this

```
bin/

etc/bspwm/
etc/dunst/
etc/home.d/
etc/gtk-3.0/
etc/nvim/init.vim
etc/nvim/coc-settings.json
etc/picom/
etc/sh/
etc/sxhkd/
etc/wal/
etc/xorg.d/
etc/pythonrc
etc/trackfile

var/local/share/applications/

.profile
```

When I want to commit my dotfiles I can do `dots add $(cat etc/trackfile)`, then `dots commit -m "update"`. If I need to remove a file from my dotfiles (which is not that common), I just unlist the file then delete it from the repo with `dots rm --cached ~/path/to/file`.
