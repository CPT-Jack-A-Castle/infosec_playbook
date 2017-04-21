## ID: 100001

## HF

## Source: IDS

## Category: Policy

## Description: DHCP Starvation

## Objective Statement:
DHCP Starvation occurs when an attacker requests every single possible IP address from a DHCP server. 
If an attacker is able to trick the DHCP into giving it all its IP's then the DHCP server will have no other IP's to give to new devices that connect on the network. These new devices will not be able to use the network.  Existing devices are not affected by this attack.

## Result Analysis:
To verify the attack of this play check DHCP logs, a high number of DHCP requests over a short period of time are highly suspect. If every IP has been requested, including already leased IP's, and if every IP of the subnetwork is request a DHCP attack has been attempted.  If the DHCP server granted IPs to the attack, the attack was successful.

## Mitigation

- Port security on Switches. Assign a port a specific IP, an only allow a specific MAC address
- http://www.sciencedirect.com/science/article/pii/S0045790612001140 
- http://www.revolutionwifi.net/revolutionwifi/2011/03/preventing-dhcp-starvation-attacks.html



## Data Query Code
- DHCP Starvation
- DHCP Denial of Service (DOS)
