# Open Redirect Vulnerability

## Description
Open redirect vulnerabilities occur when a web application accepts user-controllable input that specifies a link to an external site and uses that link in a redirect. This vulnerability can be exploited by attackers to redirect users to malicious websites while making the URL appear legitimate.

## Common Vulnerabilities
- Unvalidated redirect parameters (e.g., `?url=`, `?redirect=`, `?next=`)
- Return URL manipulation in authentication flows
- Post-login redirects
- Logout redirects
- URL parameter injection
- Header-based redirects (e.g., Location, Refresh headers)

## Impact
- Phishing attacks
- Credential theft
- Malware distribution
- Bypassing security controls (e.g., URL whitelisting)
- Social engineering attacks

## Testing Approach
1. Identify redirect parameters in URLs (e.g., `url`, `redirect`, `next`, `return`, `continue`)
2. Test with external URLs (e.g., `http://evil.com`)
3. Try various encoding techniques to bypass filters
4. Test protocol handlers (e.g., `javascript:`, `data:`)
5. Test absolute and relative paths
6. Check POST-based redirects in addition to GET parameters

## Prevention
- Avoid using user-supplied input for redirects
- Use a mapping of allowed redirect destinations
- Validate redirect URLs against a whitelist
- Use relative URLs where possible
- Implement proper input validation and sanitization
