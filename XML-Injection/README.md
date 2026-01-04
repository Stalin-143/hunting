# XML Injection

## Description
XML Injection vulnerabilities occur when user-supplied data is inserted into XML documents without proper validation or sanitization. This can lead to XML External Entity (XXE) attacks, XML injection attacks, and other security issues.

## Common Attack Vectors
- XML External Entity (XXE) injection
- XML structure manipulation
- SOAP injection
- XPath injection via XML
- XML Entity Expansion (Billion Laughs attack)

## Testing Approach
Test XML input fields, file uploads, and APIs that accept XML data. Try injecting malicious XML entities and structures to manipulate the application behavior.

## Payloads
See `xml-injection-payloads.txt` for a comprehensive list of XML injection payloads.
