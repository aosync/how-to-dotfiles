# dots

Little wrapper to manage dotfiles easily using the git bare repo method.

## Installation

Symlink `dots` to a PATH-ed directory.

## How to use

Create a trackfile where you'd list the files and directories you want to be in your repository.  
By default, the file would be at `.config/trackfile` but the program handles XDG vars and the trackfile location can be overwritten with `DOTS_TRACKFILE` environment var.  

The dots repo is created and managed at `.local/share/dots` but it can be overriden with `DOTS_REPO` env var.  

The first time the git bare repo is created, you must set your repo remote url with `dots set-remote <url to remote>`.  

Then you can track your changed files with `dots track`, then push to remote with `dots push`.  

## Notes

The program handles the removing of files from the trackfile so no need to `dots rm --cached (...)` anymore.  
The program stores an old version of the trackfile in order to compare changes and delete what has been removed from the new one.  

The program also handles spaces in file names `:)`  

If you need to access git subcommands, you can do so with `--`, for example `dots -- status`.
