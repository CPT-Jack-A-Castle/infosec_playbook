## ID: 400004

## HF

## Source: IDS

## Category: Policy

## Description: VNC authentication bypass

## Objective Statement:
In this event a vulnerable version of RealVNC, which is a remote desktop application was exploited. The vulnerability allowed the attacker to connect to the VNC server and get remote desktop access without authentication.  This is very serious, if the PC is unlocked the attacker can hijack the computer, they are able to use the computer as if it is their own. They can use the mouse and keyboard and can see any applications.  The attacker can do numerous things such as extract data, read emails, place keylogger and get user credentials.

## Result Analysis:
This incident relies on Version 4.1.1 of RealVNC. The attacker can bypass authentication.  To investigate this look at firewall, ids and network logs for RealVNC associated traffic, RDP (remote desktop protocol). Look at RealVNC logs on the system running it. Because the attacker had full access the computer and any services and account credentials on it are compromised. The system should be rebuilt, accounts should be deleted and recreated. If this is not feasilable a complete scan for any malware as well as Windows Registry and event log analysis should be conducted to determine what the attacker did, and how to reverse and remove anything malicious.

## Mitigation
- Do not sure RealVNC version 4.1.1.
- Before installing other VNC versions check online to see if they are vulnerable
- Use the most up to date version as possible and always update when possible
- If RealVNC is no longer up to date or drops support, switch Remote Desktop Software

## Data Query Code
- RealVNC 4.1.1
- authentication bypass
- Remote Desktop Protocol RDP
