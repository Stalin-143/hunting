# A03 - Injection

## Description
Injection flaws occur when untrusted data is sent to an interpreter as part of a command or query. The attacker's hostile data can trick the interpreter into executing unintended commands or accessing data without proper authorization.

## Common Injection Types
- SQL Injection
- Cross-Site Scripting (XSS)
- Command Injection
- LDAP Injection
- XML Injection
- Template Injection

## Testing Approach
Submit malicious input containing special characters and observe application behavior, error messages, and response times.
