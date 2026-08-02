# Tools List

|          Tool         |  Description  |
|  -------------------  |  -----------  |
|  PowerView/SharpView  |  A PowerShell tool and a .NET port of the same used to gain situational awareness in AD. These tools can be used as replacements for various Windows net* commands and more. PowerView and SharpView can help us gather much of the data that BloodHound does, but it requires more work to make meaningful relationships among all of the data points. These tools are great for checking what additional access we may have with a new set of creds, targeting specific users or computers, or finding some "quick wins" such as users that can be attacked via Kerberoasting or ASREPRoasting. This is better for the OSCP testing environment not because Bloodhound is a banned tool, but because Bloodhound is easily overkill. |
|       BloodHound      |  Used to visually map out AD relationships and help plan attack paths that may otherwise go unnoticed. Uses the SharpHound PowerShell or C# ingestor to gather data to later be imported into the BloodHound Javascript (Electron) application with a Neo4j database for graphical analysis of the AD environment. A useful tool to play with, but again it's overkill for the OSCP scenario.  |
|       SharpHound      | The C# data collector that gathers information from Active Directory about varying AD objects such as users, groups, computers, ACLs, GPOs, user and computer attributes, user sessions, and more. The tool produces JSON files which can then be ingested into the BloodHound GUI tool for visual analysis.  |
|      Bloodhound.py    |  A Python-based BloodHound ingestor based on the Impacket toolkit. It supports most BloodHound collection methods and can be run from a non-domain joined attack host. The output can be ingested into the BloodHound GUI for analysis. Where SharpHound must be executed directly on a Windows system joined to the target domain (or via a native Windows command prompt/C2 payload). Bloodhound.py can be executed remotely from a Linux or non-Windows machine.  |
|        Kerbrute       |  A tool written in Go that uses Kerberos Pre-Authentication to enumerate AD accounts, perform password spraying, and brute-forcing.  |
|    Impacket toolkit   |  A collection of tools written in Python for interacting with network protocols. The suite of tools contains various scripts for enumerating and attacking AD.  |
|  Responder (DON'T USE THIS)  |  Responder is a purpose-built tool to poison LLMNT, NBT-NS, and MDNS, with many different functions. THIS IS BANNED ON THE OSCP. ALL POISONING TOOLS ARE BANNED. I included this to mark it explicitly to NOT USE IT.  |
|  Inveigh.ps1 (DON'T USE THIS)  |  Similar to Responder, this is a PowerShell tool for performing network spoofing and poisoning. THIS IS BANNED ON THE OSCP. ALL POISONING TOOLS ARE BANNED.  |
|  C# Inveigh (InveighZero) (DON'T USE THIS)  |  The C# version of Inveigh with a semi-interactive console for interacting with captured data such as username and password hashes. BANNED ON THE OSCP.  |
|        rpcinfo        |  The rpcinfo utility is used to query the status of an RPC program or enumerate the list of available RPC services on a remote host. The "-p" option is used to specify the target host. For example the command "rpcinfo -p 10.0.0.1" will return a list of all the RPC services available on the remote host, along with their program number, version number, and protocol. Note that this command must be run with sufficient privileges.  |
|       rpcclient       |  A part of the Samba suite on Linux distros that can be used to perform a variety of AD enum tasks via the remote RPC service.  |
|   CrackMapExec (CME)  |  CME is an enum, attack, and post-exploit toolkit which can help greatly in enum and performing attacks with the data we gather. CME attempts to "Live off the land" and abuse built-in features and protocols like SMB, WMI, WinRM, and MSSQL.  |
|         Rubeus        |  A C# tool built for Kerberos Abuse  |
|     GetUserSPNs.py    |  An Impacket module geared towards finding Service Principal names tied to normal users. DO NOT USE ON THE OSCP.  |
|        Hashcat        |  A great hash cracking and password recovery tool.  |
|       enum4linux      |  A tool for enumerating information from Windows and Samba systems.  |
|     enum4linux-ng     |  A rework of the OG Enum4linux tool that works a bit differently.  |
|       ldapsearch      |  Built-in interface for interacting with the LDAP protocol.  |
|      windapsearch     |  A Python script used to enum AD users, groups, and computers using LDAP queries. Useful for automating custom LDAP queries.  |
|  DomainPasswordSpray.ps1  |  DomainPasswordSpray is a tool written in PowerShell to perform a password spray attack against users of a domain  |
|      LAPSToolkit      |  The toolkit includes functions written in PowerShell that leverage PowerView to audit and attack Active Directory environments that have deployed Microsoft's Local Administrator Password Solution (LAPS).  |
|         smbmap        |  SMB share enumeration across a domain  |
|       psexec.py       |  Part of the Impacket toolkit, it provides us with Psexec-Like functionality in the form of a semi-interactive shell.  |
|       wmiexec.py      |  Part of the Impacket toolkit, it provides the capability of command execution over WMI.  |
|        Snaffler       |  Useful for finding information (such as credentials) in AD on computers with accessible file shares.  |
