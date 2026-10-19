Once we connect to a shell through Netcat, we will notice that we can only type commands or backspace, but we cannot move the text cursor left or right to edit our commands, nor can w ego up and down to access the command history. This is a problem solved by upgrading the TTY by mapping our terminal TTY with the remote TTY.

Python example: python -c 'import pty; pty.spawn("/bin/bash")'

^ After running this command, we will hit ctrl+z to background our shell and get back on our local terminal, and input the following stty command.

nc -lvnp 1234

stty raw -echo

fg 

Once we hit fg, it will bring back our netcat shell to the foreground. At this point, the terminal will show a blank line. We can hit enter again to get back to our shell or input reset and hit enter to bring it back. At this point, we would have a fully working TTY shell with command history and everything else.

[enter]

[enter]

We may notice that our shell does not cover the entire terminal. To fix this, we need to figure out a few variables. We can open another terminal window on our system, maximize the windows or use any size we want, and then input the following commands to get our variables:

echo $TERM

xterm-256color

stty size

Go back to the netcat shell and use the following command to correct them:

export TERM=[OUTPUT]

stty rows [FIRST NUMBER] columns [second number]

Once we do that, we should have a netcat shell that uses the terminal's full features, just like an SSH connection.

Python pty, stty raw -echo, and script-based shell stabilization commands.
