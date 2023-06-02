# Time of last executed command in Ubuntu
This modification of bash.rc displays time of the last executed command in command's window title. 
This works as it is showed at below gif:

<img src="/images/visualization.gif" alt="Time of the last executed command">

## How to use it?

Replace below code from .bashrc file:
```
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac
```

By this code:

```
# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]1;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    # Set the title to hh:mm:ss user@host:dir
    # Note: hh:mm:ss is time of last execcuted command
    PROMPT_COMMAND='echo -ne "\e]2;$(date +"%T") ${USER}@${HOSTNAME}: ${PWD}\a"'
    ;;
*)
    ;;
esac
```

