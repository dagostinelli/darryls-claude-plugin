# Security Audit

Use subagents (the Agent tool) to parallelize this work where possible.

Perform a comprehensive security audit of the current code or changes:
- Check for OWASP Top 10 vulnerabilities (SQL injection, XSS, CSRF, etc.)
- Review authentication and authorization logic
- Look for sensitive data exposure (hardcoded secrets, API keys, passwords)
- Check input validation and sanitization
- Review error handling for information leakage
- Identify insecure dependencies or outdated libraries
- Check for insecure cryptographic practices

Provide severity ratings and remediation steps for each finding.

If there are a CONVENTIONS.md and/or an ARCHITECTURE.md file, use them to help you make smart recommendations for this project.
