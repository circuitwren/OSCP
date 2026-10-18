The most common type of shell, the reverse shell, is the quickest and easiest method to obtain control over a compromised host. Once we identify a vulnerability on the remote host that allows remote code execution, we can start a netcat listener on our machine that listens on that specific port ex -4444. With this listener in place, we can execute a reverse shell command, that connects the remote systems shell to our netcat listener, which in turn gives us a reverse connection over the remote system.

The command we execute is dependent on what OS the compromised host runs on and what applications and commands we can access.

https://swisskyrepo.github.io/InternalAllTheThings/cheatsheets/shell-reverse-cheatsheet/#c

Once we utilize the exploit we have over the remote hosts we should receive a connection in the netcat listener.

A reverse shell is handy when we want to get a quick, reliable connection to our compromised host. However, a Reverse Shell can be very fragile. Once the reverse shell command is stopped, or if we lose our connection for any reason, we would have to use the initial exploit to execute the reverse shell command again to regain our access.
