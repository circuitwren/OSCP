**Set IP**
1. `export IP="<TARGET IP>"`
2. Everytime you need to type the IP in the terminal simply use `$IP`.


   Example: `sudo nmap -p- --min-rate 3000 --open -Pn -oG [CHOSEN FILE PATH]/all-tcp.gnmap $IP`


NOTE: This does not carry over into each terminal. This must be scripted into each tmux window initally.

**NMAP**

1. Terminal 1 (TCP): `sudo nmap -p- --min-rate 3000 --open -Pn -oG [CHOSEN FILE PATH]/all-tcp.gnmap <TARGET-IP>`
2. Terminal 2 (UDP): `sudo nmap -sU --top-ports 200 --min-rate 1000 -Pn -oN [CHOSEN FILE PATH]/udp-top200.txt <TARGET-IP>`

**Linux Network Commands**

Syntax = ip [options] OBJECT {COMMAND | help}

• `ip a` - Displays details such as int names, MAC addresses, ipv4 and ipv6 addresses, subnet masks and more.

• `sudo ip addr add 192.168.x.x/24 dev eth0` - Adds the IP address 192.168.x.x with a subnet mask of 24 to the eth0 interface.

• `sudo ip route delete 10.0.0.0/24 via 192.168.1.1 dev eth0` - Removes the route 10.0.0.0/24 network via the gateway 192.168.1.1 through the eth0 interface.

• `sudo ip route add default via 192.168.1.254 dev eth0` - Sets 192.168.1.254 as the new default gateway through the etho0 interface.

• `sudo ip link set eth0 up` - Brings the eth0 interface up, enabling it to send and receive network traffic.

• `sudo ip link set eth0 mtu 1500` - Sets the MTU of the eth0 interface to 1500 bytes.

• `watch -n 1 “ip -s link show eth0 | grep ‘RX bytes’”` - Continuously monitors the receive (RX) traffic on the eth0 interface, updating every second.

• `ip -s link show eth0 | grep -E ‘errors|dropped’` - Shows stats related to packet errors and dropped packs on the eth0 interface.

• `ip monitor` - Monitors and displays the state of devices, addresses, and routes continuously.

• `ip neighbour` - Used to view the MAC address of the devices connected to your system.

   ◇ `STALE`: The neighbor is valid, but is probably already unreachable, so the kernel will try to check it at the first transmission.
   
   ◇ `REACHABLE`: This means that the neighbor is valid and reachable.
   
   ◇ `DELAY`: This means that a packet has been sent to the stable neighbor and the kernel is waiting for confirmation.
   
• `ip neighbour del (ip_add) dev interface` - Deletes an ARP entry.

• `ip neighbour add (ip_add) dev interface` - Adds an ARP entry.

Source: https://www.geeksforgeeks.org/linux-unix/ip-command-in-linux-with-examples/

<img width="732" height="960" alt="image" src="https://github.com/user-attachments/assets/e2da8185-eb1a-49d9-8bcd-73f2bb439839" />

Source:  https://wizardzines.com/comics/#:~:text=★%20wizard%20zines%20★,of%20the%20comics%20I%27ve%20published!
