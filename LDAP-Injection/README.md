# LDAP Injection

## Description
LDAP Injection is an attack used to exploit web applications that construct LDAP statements based on user input. When an application fails to properly sanitize user input, it's possible to modify LDAP statements through techniques similar to SQL injection.

## Common Attack Vectors
- Login forms
- Search fields
- User directory lookups
- Authentication systems

## Testing Approach
Submit LDAP metacharacters and operators in input fields to test if the application is vulnerable to LDAP injection.

## Payloads
See `ldap-injection-payloads.txt` for a comprehensive list of LDAP injection payloads.
