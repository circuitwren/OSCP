Since Nmap is free, the only barrier to port scanning mastery is knowledge.

1. Most of the scan types are only available to privileged users.
2. While Nmap attempts to produce accurate results, all of its insights are based on packets returned by the target machines (or firewalls in front of them). Such hosts may be untrustworthy and send responses intended to confuse or mislead.
3. Port scan type options are of the form -s<_C_>, where <_C_> is a prominent character in the scan name, usually the first.
4. By default Nmap performs a SYN scan, though it substitutes a connect scan if the user does not have proper privileges to send raw packets.

Scan Options:
-sS (TCP SYN scan)
  SYN scan is the default and most popular. It can be performed quickly, scanning thousands of ports per second. It is also relatively unobtrusive and stealthy since it never completes TCP connections. Often referred to as a half-open scan, because you don't open a full TCP connection. You send a SYN packet, as if you are going to open a real connection and then wait for a response.

-sT (TCP connect scan)
  TCP connect scan is the default TCP scan type when SYN scan is not an option. This is the case when a user does not have raw pack privileges.The system call completes connections to open target ports rather than performing the half-open reset that SYN scan does. Not only does this take longer, but target machines are more likely to pick up on the connection and log it. A decent IDS will catch either.

-sU (UDP scans)
  While most popular services on the Internet run over the TCP protocol, UDP services are widely deployed. DNS, SNMP, and DHCP are three of the most common. Because UDP scanning is generally slower and more difficult than TCP, some security auditors ignore these ports. Version detection (-sV) can be used to help differentiate the truly open ports from the filtered ones. A big challenge with UDP scanning is doing it quickly. Open and filtered ports rarely send any response, leaving Nmap to time out and then conduct retransmissions just in case the probe or response were lost. Closed ports are often an even bigger problem. They usually send back an ICMP port unreachable error. But unlike the RST packets sent by closed TCP ports in response to a SYN or a connect scan, many hosts rate limit ICMP pot unreachable messages by default. Ideas for speeding UDP scans up include scanning more hosts in parallel, doing a quick scan of just the popular ports first, scanning from behind the firewall, and using --host-timeout to skip slow hosts.

-sY (SCTP INIT scan)
  SCTP is a relatively new alternative to the TCP and UDP protocols, combining most characteristics of TCP and UDP, and also adding new features like multi-homing and multi-streaming. It is mostly being used for SS7/SIGTRAN services but has the potential to be used for other applications as well. SCTP INIT scan is the SCTP equivalent of a TCP SYN scan. It can be performed quickly, scanning thousands of ports per second on a fast network. Like SYN scan, INIT scan is relatively unobtrusive and stealthy, since it never completes SCTP associations. Active Directory architecture relies strictly on TCP and UDP for all of its internal and external communications, therefore this scan type will not be necessary for the OSCP.

-sN; -sF; -sX (TCP NULL, FIN, and Xmas scans)
  These three scan types exploit a loophole in the TCP RFC. When scanning systems compliant with the TCP RFC any packet NOT containing SYN, RST, or ACK bits will result in a returned RST IF the port is closed and no response at all if the port is open. So in this case a lack of response is a good thing.


  -sN (Null)
  Does not set any bits (TCP flag header is 0)
  -sF (FIN)
  Sets just the TCP FIN bit
  -sX (xmas)
  Sets the FIN, PSH, and URG flags, lighting the packet up like a Christmas tree.

  
  The key advantage to these scans is that they can sneak through certain non-stateful firewalls and packet filtering routers. Another advantage is that these scan types are a little more stealthy than even a SYN scan, however, most modern IDS products can be configured to detect them. The big downside is that not all systems follow RFC 793 to the letter. A number of systems send RST responses to the probes regardless of whether the port is open or not which then causes all of the ports to be labeled as CLOSED. This scan tends to work more often when used against Unix-based systems. Another downside is that these scans can't distinguish open ports from certain filtered ones, returning the unhelpful Schrodinger response of open|filtered.

-sW (TCP Window scan)
  Window scan is exactly the same as an ACK scan except that it exploits an implementation detail of certain systems to differentiate open ports from closed ones, rather than always printing unfiltered when an RST is returned. This scan relies on an implementation detail of a minority of systems so it can't always be trusted. Systems that don't support it will usually return all ports closed.

-sM (TCP Maimon scan)
  The Maimon scan is named after its discoverer, Uriel Maimon. This technique is exactly the same as NULL, FIN, and Xmas scans, except that the probe is FIN/ACK. Many BSD-derived systems simply drop the packet if the port is open.

--scanflags (Custom TCP scan)
  This option allows us to design our own scans by specifying arbitrary TCP flags. This gets around vendors who simply paged through the Nmap man page adding specific rules. This argument can be a numerical flag value such as 9 (PSH and FIN), but using symbolic names is easier. Just mash together any combo of URG, ACK, PSH, RST, SYN, and/or FIN in no specific order. Ex: --scanflags URGACKPSHRSTSYNFIN sets everything.

-sZ (SCTP COOKIE ECHO scan)
  This is a more advanced SCTP scan. It takes advantage of the fact that SCTP implementations should silently drop packets containing COOKIE ECHO chunks on open ports but sends ABORT if the port is closed. Again, SCTP is not used in AD implementations and can be disregarded for the purpose of this test.

Once we identify the services running on ports identified from the Nmap scan, the next step is to look if any of the apps/services have public exploits. 

Ex: Google search "windows 7 smb exploit"
A well-known tool for this purpose is searchsploit.

Online resources:
* Exploit DB - https://www.exploit-db.com/
* Rapid7 - https://www.rapid7.com/db/
* Vulnerability Lab - https://www.vulnerability-lab.com/ 

MSF is an excellent tool for pentesters.
msfconsole to run
search exploit "EXAMPLE"
use exploit/windows/smb/EXAMPLE
show options
