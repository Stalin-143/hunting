# A01 - Broken Access Control

## Description
Access control enforces policy such that users cannot act outside of their intended permissions. Failures typically lead to unauthorized information disclosure, modification, or destruction of all data or performing a business function outside the user's limits.

## Common Vulnerabilities
- Path Traversal
- IDOR (Insecure Direct Object References)
- Missing Function Level Access Control
- Forced Browsing
- Privilege Escalation

## Testing Approach
Test for access control by manipulating URLs, parameters, and attempting to access resources without proper authorization.
