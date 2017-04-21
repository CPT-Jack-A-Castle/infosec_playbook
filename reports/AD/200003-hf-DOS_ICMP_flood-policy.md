## ID: 200003

## HF

## Source: IDS

## Category: Policy

## Description: DOS via ICMP Flood

## Objective Statement:
This alert was triggered because a rate limit threshold on ICMP packets was detected.  While this attack can occur on other systems this attack is more serious for Windows computers.  Due to poor networking in the Windows operating system when a high number of ping requests are sent the computer can freeze and crash, requiring a reboot to get back to working order.
If this occurs on an Active Directory server, or windows system that has a critical service it can impeded the entire organizations success.  Web servers, file shares and even the ability to log into computers that require Domain access to login will seize to work.


## Result Analysis:
Windows has a poor implementation of the networking stack, when a sufficient, 10,000-20,000 ICMP type 3 code 3 (echo request) packets are sent to the Windows machine it will generate high enough CPU load to crash and freeze the target machine.  To investigate this attack review Firewall, IDS, and network logs to find the attacker. If they are internal investigate the root cause such as malware, unauthorized machine, compromised user account, or malicious user within the organization. If it is external investigate the IP address, is it associate with other attacks recently, what other traffic has it generated against your network. It could be an attacker trying to gain access, or one that already has access to the network.
While 10,000 to 20,000 ICMP packets may sound like alot, 50Mbits per second can generate 40,000 to 50,000 packets per second. This is not a high bandwith DOS attack and is easy to perform.


*References for Futher Learning*
- http://blacknurse.dk/
- https://isc.sans.edu/forums/diary/ICMP+Unreachable+DoS+Attacks+aka+Black+Nurse/21699/
- http://www.netresec.com/?page=Blog&month=2016-11&post=BlackNurse-Denial-of-Service-Attack
- https://blog.fortinet.com/2016/11/14/black-nurse-ddos-attack-power-of-granular-packet-inspection-of-fortiddos-with-unpredictable-ddos-attacks

## Mitigation
- Implement Firewall rate limiting
- If pinging is not required from external network, block it with firewall or IPS
- There are various patches for Windows, and other devices that are suspectible to this style of attack.



## Data Query Code
- Flood
- Denial of Service (DOS)
- ICMP Flood
- BlackNurse
