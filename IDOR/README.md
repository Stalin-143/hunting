# IDOR (Insecure Direct Object References)

## Description
Insecure Direct Object References (IDOR) occur when an application provides direct access to objects based on user-supplied input. As a result, attackers can bypass authorization and access resources directly by modifying the value of a parameter used to point to an object.

## Common Attack Vectors
- URL parameters (IDs, usernames)
- API endpoints
- File references
- Database keys
- Session tokens

## Testing Approach
Manipulate object references (IDs, filenames, keys) to access unauthorized resources belonging to other users.

## Payloads
See `idor-payloads.txt` for a comprehensive list of IDOR testing techniques and payloads.
