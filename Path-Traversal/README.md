# Path Traversal

## Description
Path traversal (also known as directory traversal) is a web security vulnerability that allows an attacker to read arbitrary files on the server that is running an application. This might include application code and data, credentials for back-end systems, and sensitive operating system files.

## Common Attack Vectors
- File download functionality
- File upload functionality
- Template inclusion
- Image/document display features
- Static resource serving

## Testing Approach
Submit path traversal sequences (../, ..\.., etc.) in file parameters to attempt to access files outside the intended directory.

## Payloads
See `path-traversal-payloads.txt` for a comprehensive list of path traversal payloads.
