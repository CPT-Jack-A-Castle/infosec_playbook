## ID: 500004

## INV

## Source: IDS

## Category: Suspect

## Description: DNS Caching Poison

## Objective Statement:
This alert detected a burst amount of suspicious traffic being sent to the DNS caching server.  The traffic was to update the records of the caching server, with spoofed IP address. The suspected attacker may have faked the IP address of the master DNS server where the caching DNS server gets its updates from.


## Result Analysis:
Investigate the traffic that was sent, and investigate the DNS cache records on the DNS caching server. If this was an attacker the domains and IP's will likely have been edited to resolve to the IP address the attacker specified.  Once it has been discovered what the user changed, check to see if users on your network requested those any of those records by checking both the DNS caching query logs and any full content data available for the network.  Investigate the contents of the website, or whatever service the IP was running. Investigate any workstations or computers that communicated with this IP address. They may be infected with malware.


## Mitigation
- Implement better firewall rules to check for spoofed traffic
- Implement port security so spoofing cannot occur, or is detered

## Data Query Code
- DNS Cache Poison
- DNS malicious cache

