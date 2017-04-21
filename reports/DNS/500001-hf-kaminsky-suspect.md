## ID: 500001

## HF

## Source: IDS

## Category: Suspect

## Description: Kaminsky DNS Bug

## Objective Statement:
This play is for the Kaminsky DNS bug that allows an attacker to reply to a request for a domains IP with a fake IP address.  The IP the attacker provides may just be simple redirection to gain add revenue from people visiting the page, or it could host malicious content such as malware that invects visitors computers. The attacker only needs to reply faster than a valid DNS server to successfully execute this attack.  


## Result Analysis:
This is based on a race condition for a DNS request.  BIND DNS Versions 4.9.2 and various older versions are vulnerable.  To investigate this further an analysis of the IP address that the user was redirected to is required.  Setup an environment that is isolated from the rest of the network, or outside and visit the IP address given to determine its nature.  Turn off javascript so that  malicious code cannot be execute on a simple site visit. Examine the site for downloadable files, user login pages that may have been used to steal credentials and the type of content.
The IP can also be checked against public blacklists and incident event reporters too learn what type of attacks and traffic it is associated with. Depending on the results the computer that visisted the website may need to be analyzed for malware, and any user credentials provided to the site should ideally be deleted and a new account created, or at the very minimal changed.  Any other accounts that use the same login credentials, such as the same email account or username should also be changed.


Snort rule that generates the alert:
```
alert udp $EXTERNAL_NET 53 -> $HOME_NET any (msg:”DNS mismatched txt string size”; byte_test:1,&,128,2; byte_test:2,>,0,6; 
reference:bugtraq,31881; reference: cve,2008-2469; classtype:attempted-admin; sid:99999;)
```


*References for Futher Learning*
- http://unixwiz.net/techtips/iguide-kaminsky-dns-vuln.html
- http://www.linuxjournal.com/content/understanding-kaminskys-dns-bug
- https://www.wired.com/2008/07/kaminsky-on-how/

## Mitigation
- Any DNS servers being hosted under your control should be upgraded if they are a vulnerable versions
- If you are using a 3rd party DNS, investigate to find out if they are vulnerable to this attack
- Consider switching DNS server providers if they are vulnerable, or providing your own service if not already in place

## Data Query Code
- Kaminsky Bug DNS
- race condition
- bad dns
- Bind DNS 4.9.2
