# Authentication guide for GitHub API

This document explains how authentication works when using the GitHub REST API v3 and how it is implemented in this project.

---

## Why Authenticate?

Authentication increases your API rate limit and allows access to private resources if needed.

- **Without authentication:** 60 requests per hour per IP address.
- **With token authentication:** 5,000 requests per hour per user.

---

## Personal Access Token (PAT)

A personal access token is required for authenticated requests. You can create one via:

1. Go to https://github.com/settings/tokens
2. Click "Generate new token"
3. Select the appropriate scopes (e.g., `public_repo`)
4. Copy and store the token securely.

---

## How to use the token in code?

Set the token in your Python script as follows:

```python
HEADERS = {
    "Authorization": f"token YOUR_GITHUB_TOKEN",
    "Accept": "application/vnd.github.v3+json"
}
```

This header must be included in each request.

---

## Best practices

- Never share or upload your token publicly.
- Use environment variables to manage secrets securely.
- Regenerate your token if it gets compromised.
