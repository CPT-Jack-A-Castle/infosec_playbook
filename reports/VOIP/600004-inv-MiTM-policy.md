## ID: 600004

## INV

## Source: IDS

## Category: Policy

## Description: Man in the Middle

## Objective Statement:
In this play the attacker was able to intercept a phone call using a man-in-the-middle technique. This meant that the call went through his machine before it continue to one of the clients on the call. The attacker can rebuild the call and listen to it.  This is serious play, as any organization secrets that were in the call are compromised. This can even include user credentials or IT help that could help an attacker gain access to the network / systems.

## Result Analysis:
The VOIP traffic is unecrypted, and users are suspectible to man in the middle attacks. Investigate the victims ARP table, if all MAC addresses resolve as 1 single IP address, or multiple MACs relate to one IP address they have been ARP posioned.  
Conduct an investigation with the call participants to determine if any organization secrets or technical information was discussed. Depending on the findings take appropriate action which can include changing system credentials, and rebuilding systems / services.

In the even that traffic is encrypted, obsfucate or encoded in some cryptic way it is still possible for the attacker to replay and listen to the call.  The attacker could have easily captured the keys that encrypted the traffic, or the the method used is not implemented securely it can be decoded or unecrypted.


*References for Futher Learning*
- https://www.veracode.com/security/man-middle-attack
- https://www.owasp.org/index.php/Man-in-the-middle_attack
- http://internetofthingsagenda.techtarget.com/definition/man-in-the-middle-attack-MitM
- http://www.thegeekstuff.com/2012/01/arp-cache-poisoning
- http://www.admin-magazine.com/Articles/Arp-Cache-Poisoning-and-Packet-Sniffing

## Mitigation
- Implement port security, this can help detect someone trying to ARP poison others
- Firewall rules to check IPs and MAC addresses to find victims and suspected attackers
- If no encryption is in place on the VOIP server take the time to properly configure and implement encryption to make it harder to extract the call data.

## Data Query Code
- Man in the middle
- mitm 
- call interception
- call listener
- unauthorized caller