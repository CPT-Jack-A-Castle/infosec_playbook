## ID: 200002

## INV

## Source: Graylog

## Category: Suspect

## Description: An AD account is locked out

## Objective Statement:
This alert was generated because an account has been locked out.  Depending on the domain settings this typically happens when a user attempts to login with bad credentials too many times.  This could be from a simple mistake like having caps lock on, typing the wrong password, forgetting the password or recently changing the password and it not having taken effect yet.
This warrants further investigation because it could mean an attacker was trying to use old passwords to login, use variations of old passwords or brute force the account credentials.



## Result Analysis:
The Graylog team captured this log from the Windows AD, it can be viewed on the Graylog web interface system or through an Active Directory Administrator account in the AD logs. Below is a sample of an alert / event for a locked out account.
The person who the account belongs too needs to be contact to determine if they are aware of the lock out and if they accidentally locked themselves out.  Event logs can also be checked for login attempts and check for the IP address, number of attempts and times between attempts.
In the links provided below there are ways provided to determine the source and cause of the account lockout if the user cannot be contacted, or takes time to contact.


Here is a sample event log for a account being locked out.
```
D.dpi911.com
MSWinEventLog? 1 Security 93669
Wed Apr 05 12:13:25 2017 4740

Microsoft-Windows-Security-Auditing N/A N/A Success Audit AD.dpi911.com User Account Management A user account was locked out. 
Subject: Security ID: S-1-5-18 Account Name: AD$ Account Domain: DPI911 Logon ID: 0x3E7 
Account That Was Locked Out: Security ID: S-1-5-21-1875060592-342617373-121947845-1105 Account Name: kyamin 
Additional Information: Caller Computer Name: MOOVEN-PC 26743
```

*References for Futher Learning*
- https://community.spiceworks.com/how_to/48758-trace-the-source-of-a-bad-password-and-account-lockout-in-ad
- https://community.spiceworks.com/how_to/128213-identify-the-source-of-account-lockouts-in-active-directory
- http://www.tomsitpro.com/articles/powershell-active-directory-lockouts,2-848.html


## Mitigation
- Users can legitimately forget their passwords, type it wrong, or use an old password by mistake. There is no mitigation for legitimate lockouts.
- Brute forcing is hard to mitigate because anyone can attempt to type passwords in while trying to guess the account. Brute force over network can be detected if it is in rapid succession or from an IP that is not associated with the user
- Port security can aide in the time it takes to determine if it was a legitmate login attempt or an attacker
- Proper Group Policy Object settings can help warn and in some cases depending on the settings prevent the brute force from being successful. 
- Restricting which computer and IP a user can log into can prevent this attack
- Review the links in the Further Learning section above for more information


## Data Query Code
- Account lockout
- locked out
- active directory
- brute force
- bad password
- wrong password
- forgotten password
- bad login