---
trigger: always_on
---

# Config

Configuration File Standards

REQUIRED: hugo.toml (modern standard)
AVOID: config.toml (legacy approach)


Pagination Configuration

REQUIRED: [pagination] object with structured settings
AVOID: Legacy paginate and paginatePath variables

github_repo_link = https://github.com/gahoccode/{repo_name}
baseURL = '{github_repo_link}' 