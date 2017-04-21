## ID: 800002

## INV

## Source: IPS

## Category: Suspect Event

## Description:
Suspected Cross Site Scripting Detected

## Objective Statement
This alert means the tag `<script>` or a variation such as `%3Cscript%3E` was detected in a user-input field or URL paramter when it should not be.
Cross-Site Scripting (XSS) is a Javascript vulnerability that allows attackers to inject code into webpages that execute on a clients web browser.  XSS attacks can be used to redirect users to a malicious file, redirect to a malicious website or run malicious code. Such as stealing credentials or session information


## Result Analysis

Basic XSS samples:
```javascript
<script>alert("danger")</script>

<script>alert("http://dangerouswebsite.com/malware.exe")</script>

<script>var cookie = document.cookie()</script>
```

To investigate these suspected events look into web server logs for POST information containing Javascript, or URLs containing Javascript in paramters.


*References for Futher Learning*

- https://www.owasp.org/index.php/Cross-site_Scripting_(XSS)


## Mitigation

- Filter and sanitize user input
- Use Web Application Firewall to detect and block XSS attacks
- URL Encode any user input data when sending to client, so that special characters are not executed
- https://www.owasp.org/index.php/XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet
- Use javascript frameworks that can handle XSS vulnerabilities (last resort)


## Data Query Code
- XSS cross site scripting
- javascript code injection
- script execution



