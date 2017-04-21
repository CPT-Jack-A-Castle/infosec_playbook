## ID: 500003

## HF

## Source: IDS

## Category: suspect

## Description: DNS Flood

## Objective Statement:
This alert was triggered because a threshold for DNS traffic, specific port and UDP protocol was exceeded. It is likely an attacker is trying to flood the DNS server to prevent it from operating.


## Result Analysis:
Check firewall, networking and IDS logs to determine who the attacker was. The IP can also be checked against public blacklists and incident event reporters too learn what type of attacks and traffic it is associated with.  If it is not an external attacker, and come from within check to see if the attacker system is infected with malware, or if it is an unauthorized computer/system or if it was a malicious user within the organization.


## Mitigation
- Implement firewall rate limiting

## Data Query Code
- DNS Flood
- DNS DOS
- Denial of Service
