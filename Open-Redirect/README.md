# Open Redirect

## Description
Open redirect vulnerabilities occur when a web application accepts user-controlled input that specifies a link to an external site and uses that link in a redirect. This can be used for phishing attacks or to bypass security controls.

## Common Attack Vectors
- URL parameters (redirect, url, return, next)
- Login/logout redirect parameters
- OAuth callback URLs
- Error page redirects

## Testing Approach
Submit external URLs in redirect parameters to test if the application redirects to arbitrary external sites.

## Payloads
See `open-redirect-payloads.txt` for a comprehensive list of open redirect payloads.
