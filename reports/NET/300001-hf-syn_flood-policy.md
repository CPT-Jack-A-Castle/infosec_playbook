## ID: 300001

## HF

## Source: IDS

## Category: Policy

## Description: DOS SYN Flood

## Objective Statement:
This alert was triggered because a rate limit threshold on the number of packets over a short period of time was exceeded. The packets were also of type "SYN" which means they are requests for new connections.  This most likely a denial of service attack attempt. While further investigation is needed to determine what happened because the rate limit was hit a denial of service did occur. The denial of service could be intentional attack or legitmate attempts by high volumes of people to connect to a service.

This is categorized as general web because it can happen to any system on the network and is not unique to any service or operating system. 

## Result Analysis:
TCP packets have a header option for the type of "Flag" to be set. The "SYN" flag is used to indicate a machine wants to initiate a connection with another machine. It is the first step of the 3 way TCP handshake.  When an attacker send many SYN requests a system will reserve memory for each connection, which takes up memory and some CPU resources.  If the attack is carried out fast enough it is also possible to exceed the limits of both the cable and the target system, preventing any another traffic. 
To further investigate check Firewall and IDS logs for the traffic sources and destinations.  Sometimes this incident is not an attack, but is legitimately caused by high number of users wanting to access something. This could be a newly released website, or product on a website that many people are waiting for. This could accidentally cause a DOS attack on the system.


*References for Futher Learning*
- http://www.cisco.com/c/en/us/about/press/internet-protocol-journal/back-issues/table-contents-34/syn-flooding-attacks.html
- https://tools.ietf.org/html/rfc4987
- https://www.incapsula.com/ddos/attack-glossary/syn-flood.html


## Mitigation
- In addition to IDS rate limit rules, firewall rate limit rules may want to be implemented
- Port security should be implemented if it is not. This can prevent attackers from utiziling open ports and narrow down the posibilites for this type of attack
- See the further learning references for more detailed information

## Data Query Code
- Denial of Service SYN Flood (DOS)
- TCP SYN flag
