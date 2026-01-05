# Server-Side Template Injection (SSTI)

## Description
Server-Side Template Injection occurs when user input is embedded in a template in an unsafe manner, allowing attackers to inject template directives and execute arbitrary code on the server. SSTI can lead to remote code execution, information disclosure, and complete server compromise.

## Common Vulnerable Template Engines
- **Jinja2** (Python - Flask, Django)
- **Twig** (PHP)
- **Freemarker** (Java)
- **Velocity** (Java)
- **Smarty** (PHP)
- **Pug/Jade** (Node.js)
- **ERB** (Ruby on Rails)
- **Thymeleaf** (Java)

## Common Attack Vectors
- User input in template rendering
- Email templates with user-controlled content
- Error messages with dynamic content
- Markdown/Wiki renderers
- PDF generators
- Report generators

## Testing Approach
1. Inject template syntax like `{{7*7}}` or `${7*7}` in input fields
2. Observe if mathematical expressions are evaluated
3. Identify the template engine through error messages or syntax
4. Escalate to code execution using engine-specific payloads

## Detection Methods
- Submit polyglot payloads: `${{<%[%'"}}%\`
- Test mathematical operations: `{{7*7}}`, `${7*7}`
- Check for template-specific syntax errors
- Analyze response differences

## Payloads
See `ssti-payloads.txt` for a comprehensive list of SSTI payloads.
