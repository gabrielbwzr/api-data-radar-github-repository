# Error Handling and Rate Limit Strategy

This document outlines the most common issues encountered while interacting with the GitHub REST API and provides strategies for troubleshooting and mitigation.

## Common Errors and Fixes

### 1. 401 Unauthorized

**Cause:**
- The GitHub token is missing, expired, or invalid.

**How to fix?:**
- Ensure the token is included in the request headers
- Regenerate the token in your GitHub Developer Settings if it has expired or been revoked.
- Confirm that the token has the correct scopes (e.g., repo or public_repo if needed).

### 2. 403 Forbidden (Rate Limit Exceeded)

**Cause:**
- GitHub's API rate limits have been exceeded.

**GitHub Rate Limits:**
- Without authentication: 60 requests per hour per IP.
- With token authentication: 5,000 requests per hour per user.

**How to fix?:**
- Always authenticate using a personal access token.
- Add delays (e.g., time.sleep(1)) between requests when iterating.
- Check your remaining quota using the headers or /rate_limit endpoint.

### 3. 404 Not Found

**Cause**
- The resource (repository, file, or endpoint) does not exist or is misspelled.

**How to fix?:**
- Double-check the endpoint path.
- Verify that the repository owner and name are correct.

### 4. 5xx Server Errors

**Cause:**
- Internal GitHub server error or temporary downtime.

**How to fix?:**
- Retry the request after a short delay.
- Implement exponential backoff retry logic if needed.

### 5. Best practices

- Use authentication to unlock higher rate limits.
- Always monitor X-RateLimit-Remaining.
- Catch and log API errors in your scripts.
- Respect the GitHub API guidelines to avoid blocking.
