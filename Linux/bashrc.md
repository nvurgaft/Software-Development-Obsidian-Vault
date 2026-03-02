The `.bashrc` file is a initialization file that is being run when a new shell session is spun up for a user

The file is an executable bash script, it can be found at `~/.bashrc`.

The file will run when a user is logging in into a session, so when the user `nick` logs in, the file at `/home/nick/.bashrc` will run.

### Excerpt

```bash
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend
...
```
