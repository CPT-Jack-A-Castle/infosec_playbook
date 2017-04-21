## ID: 200001 

## INV

## Source: AD GPO logs

## Category: Policy

## Description: Multiple IP's for the same user

## Objective Statement:
This alert was triggered because the Group Policy Objective (GPO) in Active Directory detected multiple IP's correlating to a since account currently logged into on the Domain.
Having multiple IP's could indicate that the user account is compromised, credentials were obtained and logged into on another machine.  If an attacker was able to get credentials any services like email and file shares that the active directory account had access to may be compromised.  If the active directory account had administrative privileges the entire domain can be compromised.


## Result Analysis:


This can be investigated by exploring the Active Directory, specifically the GPO alerts.  The user should be contacted to determine if they logged into the other computer.  If they did not the user account is compromised. The account should be deleted and a new account made.  This includes any other accounts and services such as email that the attack could have access.  If this is not achievable intensely review what the attack did to determine other compromised accounts.  

A review should be conducted to determine if this type of action, logging into multiple systems at once should be permitted on the network.  While there are legitmate reasons a user would log into multiple computers, it should be reassessed.  The users privileges should also be review to see if all permissions were required.


Sample alert from GPO that detected a login.

```
All messages

facility

user-level
level
6
message

AD.dpi911.com MSWinEventLog? 1 Security 94922 Wed Apr 05 12:51:40 2017 4769 Microsoft-Windows-Security-Auditing 
N/A N/A Success Audit AD.dpi911.com Kerberos Service Ticket Operations A Kerberos service ticket was requested. 
Account Information: Account Name: malin4@DPI911.COM Account Domain: DPI911.COM 
Logon GUID: {0D0040BA-8166-6865-21EB-4F483A569601} 
Service Information: Service Name: MOOVEN-PC$ 
Service ID: S-1-5-21-1875060592-342617373-121947845-1137 
Network Information: Client Address: ::ffff:192.168.1.235 
Client Port: 49168 Additional Information: Ticket Options: 0x40810000 
Ticket Encryption Type: 0x17 Failure Code: 0x0 Transited Services: - 

```

## Mitigation
- GPO has security settings to detect this activity and generate alerts
- GPO security settings can be configured to disallow multiple loginsff
- http://windowsitpro.com/group-policy/gpo-security
- https://technet.microsoft.com/en-ca/library/cc960657.aspx



## Data Query Code
- Multiple IPs 
- Multiple Logins
- User logged in multiple times
- Multiple account logins
- GPO
- Group Policy Object