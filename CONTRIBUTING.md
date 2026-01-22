# 🤝 Contributing to Hunting-

Thank you for your interest in contributing to this security testing repository! We welcome contributions that help make this resource more comprehensive and valuable for the security community.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Contribution Guidelines](#contribution-guidelines)
- [Adding New Payloads](#adding-new-payloads)
- [Creating New Categories](#creating-new-categories)
- [Submission Process](#submission-process)
- [Quality Standards](#quality-standards)

## 🤝 Code of Conduct

### Our Standards

- **Be Ethical**: All contributions must be for legitimate security testing purposes
- **Be Respectful**: Treat all contributors with respect and professionalism
- **Be Legal**: Only contribute content that is legal and ethical
- **Be Helpful**: Focus on educational value and practical security testing
- **Be Accurate**: Ensure all payloads and techniques are properly documented

### Prohibited Content

Do NOT contribute:
- Illegal or malicious content
- Personal information or credentials from unauthorized sources
- Exploits for 0-day vulnerabilities before responsible disclosure
- Content that encourages illegal activities
- Plagiarized content without proper attribution

## 💡 How Can I Contribute?

### Types of Contributions

1. **New Payloads**: Add new security testing payloads to existing categories
2. **New Categories**: Propose and create new vulnerability categories
3. **Documentation**: Improve README files and explanations
4. **Bug Fixes**: Correct errors in existing payloads or documentation
5. **Organization**: Improve structure and organization of content
6. **Examples**: Add real-world examples and use cases

## 📝 Contribution Guidelines

### General Rules

1. **Quality Over Quantity**: Focus on well-tested, effective payloads
2. **Clear Documentation**: Each payload should be clearly explained
3. **Proper Attribution**: Credit original sources when applicable
4. **Educational Focus**: Include context about when and how to use payloads
5. **Organized Structure**: Follow the existing repository structure
6. **Legal Compliance**: Ensure all content complies with applicable laws

### Content Requirements

- **Relevance**: Content must be relevant to security testing
- **Accuracy**: Payloads should be tested and verified when possible
- **Clarity**: Use clear, descriptive naming and organization
- **Context**: Provide background information about attack vectors
- **Safety**: Include warnings about potential impacts

## 🎯 Adding New Payloads

### Step-by-Step Process

1. **Identify the Category**: Determine which existing category fits your payload
2. **Check for Duplicates**: Ensure the payload doesn't already exist
3. **Format Properly**: Follow the formatting style of existing payloads
4. **Add Context**: Include comments explaining complex payloads when needed
5. **Test if Possible**: Verify payloads work in authorized testing environments

### Payload Format

```
## Section Name
payload_1
payload_2
payload_3

## Another Section
payload_with_description
# Comment explaining complex payload
another_payload
```

### Example Addition

```
## DOM-Based XSS
<img src=x onerror=alert(document.domain)>
<svg/onload=alert(1)>
javascript:alert(document.cookie)
```

## 📁 Creating New Categories

### When to Create a New Category

Create a new category when:
- The vulnerability type doesn't fit existing categories
- There's substantial content (15+ unique payloads)
- The category represents a distinct attack vector
- It provides significant educational value

### New Category Structure

```
New-Category/
├── README.md
└── new-category-payloads.txt
```

### README.md Template

```markdown
# Category Name

## Description
Brief description of the vulnerability type.

## Common Attack Vectors
- Vector 1
- Vector 2
- Vector 3

## Testing Approach
How to test for this vulnerability.

## Payloads
See `category-payloads.txt` for comprehensive list.
```

## 🔄 Submission Process

### Step 1: Fork the Repository

```bash
# Fork on GitHub, then clone your fork
git clone https://github.com/YOUR-USERNAME/Hunting-.git
cd Hunting-
```

### Step 2: Create a Branch

```bash
# Create a descriptive branch name
git checkout -b add-xss-payloads
# or
git checkout -b new-category-api-injection
```

### Step 3: Make Your Changes

- Add your payloads or create new files
- Follow the existing structure and format
- Update the main README.md if adding a new category
- Test your changes locally

### Step 4: Commit Your Changes

```bash
git add .
git commit -m "Add new XSS payloads for DOM manipulation"
# Use clear, descriptive commit messages
```

### Step 5: Push and Create Pull Request

```bash
git push origin add-xss-payloads
```

Then create a Pull Request on GitHub with:
- **Clear Title**: Describe what you're adding
- **Description**: Explain the changes and why they're valuable
- **Testing**: Mention if you've tested the payloads
- **References**: Link to any relevant sources or documentation

## ✅ Quality Standards

### Before Submitting

- [ ] Payloads are properly formatted
- [ ] No duplicates exist
- [ ] Documentation is clear and accurate
- [ ] Follows existing structure and conventions
- [ ] Commit messages are descriptive
- [ ] No personal or sensitive information included
- [ ] Content is legal and ethical
- [ ] Proper attribution provided when applicable

### Review Process

1. **Initial Review**: Maintainers will review your PR
2. **Feedback**: You may receive requests for changes
3. **Updates**: Make requested changes if needed
4. **Approval**: Once approved, your PR will be merged
5. **Recognition**: Contributors will be acknowledged

## 📚 Resources

### Helpful Links

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [OWASP Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [Bug Bounty Platforms](https://www.bugcrowd.com/)
- [Responsible Disclosure Guidelines](https://cheatsheetseries.owasp.org/cheatsheets/Vulnerability_Disclosure_Cheat_Sheet.html)

### Testing Environments

Always test in authorized environments:
- Personal lab environments
- Authorized CTF platforms
- Bug bounty programs with explicit scope
- Open-source test applications (DVWA, WebGoat, etc.)

## 🎓 Learning and Growth

### For New Contributors

- Start small with simple payload additions
- Review existing content to understand the format
- Ask questions if you're unsure about anything
- Learn from feedback on your pull requests

### Best Practices

- **Stay Updated**: Keep up with latest security research
- **Be Thorough**: Research payloads before contributing
- **Collaborate**: Engage with other contributors
- **Improve**: Continuously enhance your contributions

## 📧 Contact

### Questions or Suggestions?

- **Issues**: Open a GitHub issue for discussions
- **Pull Requests**: For direct contributions
- **Security Concerns**: Report responsibly if you find issues

## 🙏 Recognition

All contributors will be recognized for their valuable contributions to the security community. Thank you for helping make this resource better!

### 🏆 Contributors Hall of Fame

We maintain a [**Contributors Hall of Fame**](./CONTRIBUTORS.md) that automatically recognizes all contributors to this project! 

**How it works:**
- When you make a contribution (pull request that gets merged), you'll automatically be added to our contributors page
- Your GitHub profile picture and username will be displayed
- The list is updated automatically via GitHub Actions
- No manual process needed - just contribute and you'll be recognized! 🌟

**What contributions count:**
- Adding new payloads or vulnerability types
- Improving documentation
- Fixing bugs or errors
- Enhancing repository organization
- Code reviews and feedback
- Any merged pull request

Check out our [Contributors Hall of Fame](./CONTRIBUTORS.md) to see all the amazing people who have contributed!

## ⚖️ Legal Reminder

By contributing to this repository, you confirm that:
- Your contributions are original or properly attributed
- You have the right to share this content
- Your contributions comply with the repository's disclaimer
- You understand the ethical and legal implications

---

**Happy Contributing! Let's build a better, more secure web together! 🚀**

*For legal disclaimers and terms of use, please see [DISCLAIMER.md](./DISCLAIMER.md)*
