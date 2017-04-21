## ID: 400002

## HF

## Source: IDS

## Category: Policy

## Description: Server Connection Queue Exhaustion DOS

## Objective Statement:
In this event an attacker was able to fill up the queue connection by connecting multiple times to the FTP server.  This prevents anyone else from acecssing the server.  This is an inconvience to the organization and anyone who needs access to the FTP server.

## Result Analysis:
In this attack the attacker create multiple connections by using multiple sources ports to connect to the FTP server.  By doing so they are eventually able to fill up the TCP State Table. No one else can connect.  Investigate the IP address by reviewing firewall, ids and network logs. Implement firewall rules to temporarily ban the attack, upon blocking the user the sessions will timeout and be free to use again.


## Mitigation
- Implement Firewall rules to detect a user connecting to the FTP server multiple times
- There is no reason for a single user to be connecting to the FTP server multiple times
- If this occurs from regular used because many people are accessing the file share, consider making a clone, separating the file share into multiple file shares, or upgrading hardware

## Data Query Code
- Denial of Service DOS
- FTP Server connection queue exhaustion
- multiple FTP connects
- TCP state table full



