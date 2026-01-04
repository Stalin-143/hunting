# NoSQL Injection

## Description
NoSQL injection is a vulnerability where an attacker can inject or manipulate NoSQL queries to bypass authentication, extract data, or perform unauthorized operations. This affects databases like MongoDB, CouchDB, Redis, Cassandra, and others that don't use traditional SQL syntax.

## Common Attack Vectors
- Authentication bypass in login forms
- Data extraction through query manipulation
- MongoDB operator injection ($ne, $gt, $regex, etc.)
- JSON/BSON injection in APIs
- Redis command injection
- CouchDB view manipulation
- Elasticsearch query injection

## Testing Approach
Submit NoSQL operators, special characters, and query manipulation attempts in:
- Login forms (username/password fields)
- Search parameters
- API endpoints accepting JSON
- Query string parameters
- Cookie values
- HTTP headers

## Common Vulnerable Patterns
- Direct user input in `find()`, `findOne()` queries
- Unvalidated JSON parsing in authentication
- Improper input sanitization in MongoDB queries
- Exposed NoSQL query interfaces

## Payloads
See `nosql-injection-payloads.txt` for a comprehensive list of NoSQL injection payloads covering:
- MongoDB injection
- CouchDB injection
- Redis injection
- Cassandra injection
- Elasticsearch injection
- Authentication bypass techniques
- Data extraction methods
