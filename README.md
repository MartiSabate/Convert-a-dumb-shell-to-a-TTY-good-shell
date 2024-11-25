# Convert-a-dumb-shell-to-a-TTY-good-shell
You can use this repository as a cheatsheet to convert a dumb tty shell to a custom one for your needs

Here you will be provided with two ways:

# Common way

- Once you have your reverse shell created, you will need to first background the current session, and then create a new stty terminal which we will configure it according to our needs:

```
```Bash
# spawn a pseudo-terminal (PTY) to emulate a physical terminal and spawn a bash shell into it
script /dev/null -c bash

# background the reverse shell
ctrl+z

# disable special character handling (ctl+c for example) and return to the reverse shell
stty raw -echo; fg

# reset the terminal configuration and set it to xterm, you can use the terminal emulator you prefer
reset xterm

# export environment variables to configure the terminal with xterm and use the bash shell
export TERM=xterm SHELL=bash

# finally set the console size according to your window size
stty rows 50 columns 235

# You can find your window size through the command `stty size`

```

# Python way

- If the victim machine allows you using Python, once the reverse shell is created you can convert it to a PRO shell through just a one liner python code to spawn a bash shell:
```
python3 -c 'import pty;pty.spawn("/bin/bash")'
```

