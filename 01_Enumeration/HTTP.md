**302 moved temporarily** means your machine does not know how to resolve the hostname to the IP address. Run this:
`sudo echo "x.x.x.x www.example.com" >> /etc/hosts`
This will map the IP to the relevant hostname.

## Gobuster

`gobuster dir -u https://example.com -w /path/to/wordlist.txt`
