Send a command to start the bind shell.
Resource: https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-bind-cheatsheet/

The example port and example IP is 1234

Next, use netcat to connect to the port and get a connection t the shell.

nc 10.10.10.1 1234

Note: Unlike a reverse shell, if we drop our connection to a bind shell for any reason, we can connect back to it and get another connection immediately. However, if the bind shell command is stopped for any reason, or if the remote host is rebooted, we would still lose our access to the remote host and will have to exploit it again to gain access.

Next step is to upgrade our TTY.
