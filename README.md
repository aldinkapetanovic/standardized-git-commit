# HOWTO

## Clone/initialize project

```sh
git init foobar

cd foobar
```

## Create/Edit commit-msg file in project's .git folder
```sh
touch .git/hooks/commit-msg
```

### File Content

```
#!/bin/bash

commit_msg_file="$1"
commit_msg=$(cat "$commit_msg_file")

# Define the regex pattern for a valid commit message format
commit_pattern="^(feature|fix|refactor|wip): .{1,50}$"

if [[ ! $commit_msg =~ $commit_pattern ]]; then
    echo "Error: Invalid commit message format. Please use 'commit_type: Your message (max 50 characters)'."
    exit 1
fi
```
## Make it executable
```sh
chmod +x .git/hooks/commit-msg
```

# Commit Message Guidelines

When making commits to this repository, please follow these guidelines:

- Use one of the following commit types:
  - `feature`: Use when adding new features.
  - `fix`: Use when fixing bugs or issues.
  - `refactor`: Use when improving existing code without adding new features or fixing issues.
  - `wip`: Use when the commit is "Work in Progress" and should not be pushed to the main branch immediately.

- Each commit message should have a maximum length of 50 characters.

- Provide a clear and concise message that describes the purpose of the commit.

Thank you for following these guidelines to maintain clarity and organization within our project.

## Test
```sh
git commit -m "Invalid commit message"

git commit -m "feature: Add some feature"
```


