## Edit commit-msg file

touch .git/hooks/commit-msg

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

chmod +x .git/hooks/commit-msg

## Test
git commit -m "Invalid commit message"

git commit -m "feature: Add some feature"
