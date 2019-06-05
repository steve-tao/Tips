# Configuration for xenodm

As indicated in the OpenBSD man page, after login **`xenodm`** will
1. run Xstartup script as root.
2. run Xsession script as a user.  This system session file may do some
additional startup and typically run the **`.xsession`** scription in the
user's home directory.

Here is a sample **_.xsession_** script
```bash
# Set up interactive shell environment
export ENV=$HOME/.kshrc

# startup Xfce
exec ck-launch-session startxfce4
```

The line ```export ENV=$HOME/.kshrc``` will call the .kshrc in the user's home
directory.

Here is a sample **_.kshrc_** script.

```bash
. /etc/ksh.kshrc

alias ls='colorls -GFh'

# Include user's private bin directory if exists
if [ -d "$HOME/.local/bin" ]; then
   if [[ $PATH != *$HOME/.local/bin* ]]; then
      PATH="$HOME/.local/bin:$PATH"
   fi
fi

# Include user's private bin directory if exists
if [ -d "$HOME/bin" ]; then
   if [[ $PATH != *$HOME/bin* ]]; then
      PATH="$HOME/bin:$PATH"
   fi
fi
export PATH
```
