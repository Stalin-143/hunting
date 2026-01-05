# CORS Misconfiguration

## Description
Cross-Origin Resource Sharing (CORS) misconfiguration occurs when a web application incorrectly configures the CORS headers, allowing unauthorized domains to access sensitive resources. This can lead to data theft, account compromise, and bypassing of the Same-Origin Policy.

## Common Misconfigurations
- **Wildcard Origin with Credentials** - `Access-Control-Allow-Origin: *` with `Access-Control-Allow-Credentials: true`
- **Null Origin Allowed** - Accepting `Origin: null`
- **Reflected Origin** - Reflecting any origin without validation
- **Subdomain Trust** - Trusting all subdomains including attacker-controlled ones
- **Pre-domain/Post-domain Trust** - Weak regex matching for origins

## Impact
- Steal sensitive user data
- Perform actions on behalf of users
- Access private API endpoints
- Read authentication tokens
- Bypass CSRF protections

## Common Attack Vectors
- API endpoints with sensitive data
- Authentication endpoints
- Profile information endpoints
- Admin panels
- Internal APIs exposed via CORS

## Testing Approach
1. Send requests with various `Origin` headers
2. Check if `Access-Control-Allow-Origin` reflects the attacker's origin
3. Verify if `Access-Control-Allow-Credentials: true` is set
4. Test with null origin, subdomains, and similar domains
5. Check for weak regex patterns in origin validation

## Payloads
See `cors-misconfiguration-payloads.txt` for a comprehensive list of CORS misconfiguration test payloads.
