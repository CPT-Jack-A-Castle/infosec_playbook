## ID: 100002

## HF

## Source: IDS

## Category: Policy

## Description: Rouge DHCP Server

## Objective Statement:
This alert was generated because IPs were being requested by and leased from a IP and mac address that is not the specified DHCP server for the network.  This means an attack is running a rouge DHCP server and assigning IP addresses to network devices.
This can disrupt network services, if domain names or IPs are being used by web servers, file shares and other services then there is a risk of the service's server being assigned the wrong IP address and not being accessible. The attacker can also assign the IP address to themself, or any device they wish imitate it.

## Result Analysis:
This is a fairly simple play to detect and investigate.  If a IP address and MAC address other than that of the specified DHCP server is being used, and it is not for temporary maintenance or change in network infrastructure there is a rouge DHCP server.
The rogue DHCP can by physically located (if it is wired) by determining which port of the switch it is plugged into and where that workstation goes.

*References for Futher Learning*
- http://tomoconnor.eu/blogish/how-to-find-rogue-dhcp-server-your-network/#.WPfpO_nytaQ
- https://documentation.meraki.com/MX-Z/DHCP/Tracking_Down_Rogue_DHCP_Servers
- https://medium.com/tech-jobs-academy/attack-a-network-by-using-a-rogue-dhcp-server-8c8acea315ab
- https://www.symantec.com/connect/downloads/detect-rogue-dhcp-servers-network


## Mitigation
- See the links in the Reference section above
- Use port security so devices obtain the IP address from the switch and cannot use another IP address
- Use firewall and IDS/IPS to block any other servers from answering DHCP traffic and requests other than the specified DHCP server.

## Data Query Code
- Rouge DHCP Server
- Malicious DHCP
- Attacker DHCP
- Fake DHCP