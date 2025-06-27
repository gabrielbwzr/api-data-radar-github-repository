# Pagination strategy for GitHub API

This document outlines how pagination is handled when querying large datasets from the GitHub REST API v3.

---

## What is pagination?

GitHub API responses are paginated when data exceeds a single response (usually 30 items by default). You must use pagination to retrieve full datasets like commits, issues, etc.

---

## Pagination parameters

The main query parameters used are:

- `per_page`: Number of results per page (maximum 100)
- `page`: Page number to retrieve

Example:

```
GET /repos/{owner}/{repo}/commits?per_page=100&page=2
```

---

## Implementation in Python

```python
def get_commits(per_page=100, max_pages=2):
    commits = []
    for page in range(1, max_pages + 1):
        url = f"{BASE_URL}/commits?per_page={per_page}&page={page}"
        response = requests.get(url, headers=HEADERS)
        if response.status_code != 200:
            break
        commits.extend(response.json())
    return commits
```

---

## Best practices

- Set `per_page=100` to reduce number of requests.
- Use a loop with a page counter and stop when no data is returned.
- Combine with rate limit checks to avoid throttling.
