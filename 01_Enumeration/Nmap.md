Once we identify the services running on ports identified from the Nmap scan, the next step is to look if any of the apps/services have public exploits. 
Ex: Google search "windows 7 smb exploit"
A well-known tool for this purpose is searchsploit.
Online resources:
Exploit DB - https://www.exploit-db.com/
Rapid7 - https://www.rapid7.com/db/
Vulnerability Lab - https://www.vulnerability-lab.com/ 

MSF is an excellent tool for pentesters.
msfconsole to run
search exploit "EXAMPLE"
use exploit/windows/smb/EXAMPLE
show options
