# A10 - Server-Side Request Forgery (SSRF)

## Description
SSRF flaws occur whenever a web application is fetching a remote resource without validating the user-supplied URL. It allows an attacker to coerce the application to send a crafted request to an unexpected destination, even when protected by a firewall, VPN, or another type of network access control list (ACL).

## Common Vulnerabilities
- Unvalidated URL parameters
- Internal network scanning
- Cloud metadata access
- Local file access via URL schemes
- Port scanning
- Service enumeration

## Testing Approach
Test URL parameters, file upload functionalities, and any feature that fetches external resources. Attempt to access internal resources, cloud metadata endpoints, and local services.
