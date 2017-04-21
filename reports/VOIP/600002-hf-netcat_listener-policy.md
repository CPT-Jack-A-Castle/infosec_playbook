## ID: 600002

## HF

## Source: IDS

## Category: Policy

## Description: Suspect traffic on a netcat listener that is connected to the database

## Objective Statement:
This alert was triggered because an attacker connected to a listening port that provides command line access as root. The attacker had complete privileges to do anything they can.  
This incident needs to be investigated to see if it was an attacker or employee who connected to the service, and what they did. It is still HF, becuase even if an employee or authorized person connected, they had root access.

## Result Analysis:
This report is quick and easy to understand, a listener running as root was connected to. Who connected and what they did can be investigate by looking for new files and recently edited files.
In one case, the attacker was able to access the database for the Asteriks VOIP service because the credentials are stored in plain text.  Check all logs for all services, because the attacker had root anything may be compromised.


## Mitigation
- Do not run listeners as root
- Turn off the listener. Use secure shells only, like SSH.

## Data Query Code
- netcat listener
- no authentication
