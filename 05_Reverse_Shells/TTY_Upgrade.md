Once we connect to a shell through Netcat, we will notice that we can only type commands or backspace, but we cannot move the text cursor left or right to edit our commands, nor can w ego up and down to access the command history. This is a problem solved by upgrading the TTY by mapping our terminal TTY with the remote TTY.

Python example: python -c 'import pty; pty.spawn("/bin/bash")'

^ After running this command, we will hit ctrl+z to background our shell and get back on our local terminal, and input the following stty command.

nc -lvnp 1234

stty raw -echo

fg 

Once we hit fg, it will bring back our netcat shell to the foreground. At this point, the terminal will show a blank line. We can hit enter again to get back to our shell or input reset and hit enter to bring it back. At this point, we would have a fully working TTY shell with command history and everything else.

[enter]

[enter]

Python pty, stty raw -echo, and script-based shell stabilization commands.
