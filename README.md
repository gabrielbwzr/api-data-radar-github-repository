# api-data-radar-github-repository
This project builds an API to extract and monitor de activity of the data in the well known Github's repository josephmisiti/awesome-machine-learning.
## Objective

Demonstrate knowledge in API data extraction, GitHub authentication, pagination, error handling, and documentation using Python and Google Colab.

---

## Tools Used

- GitHub REST API v3
- Python 3
- Google Colab
- Markdown documentation

---

## Repository structure

```
Data-Source-API-Analyst-Test/
├── README.md
├── Content/
│   ├── api_requests.ipynb
│   ├── authentication_guide.md
│   ├── error_handling_and_rate_limits.md
│   └── pagination_strategy.md
```

---

## Included documentation

- `authentication_guide.md`: How token authentication works with GitHub API
- `error_handling_and_rate_limits.md`: Handling common API errors and rate limits
- `pagination_strategy.md`: Implementation and best practices for paginated data

---

## How to run?

1. Open `Content/api_requests.ipynb` in Google Colab.
2. Once you run the first code enter your personal access token in the space required.
3. Run all cells to fetch repository info, commits, and contents.
