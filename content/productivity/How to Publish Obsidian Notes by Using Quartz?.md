---
title: How to Publish Obsidian Notes by Using Quartz?
---

## Getting Started:
1. Fork https://github.com/jackyzha0/quartz
2. Clone the repo
Resource:
https://quartz.jzhao.xyz/

## Auto Publish:

### Run sync script plus git push
1. Create a `publish-content.sh` file.
```sh

#!/bin/bash

# Run the sync-content.sh script which is outside of this repo
../sync-content.sh
wait

# Add all changes to the staging area
git add content

# Check if there are any changes
if [[ -z $(git status --porcelain) ]]; then
  echo "No changes to commit. Exiting..."
  exit 0
fi

# Commit the changes
commit_message="Sync content at $(date '+%Y-%m-%d %H:%M:%S')"
git commit -m "$commit_message"

# Push the changes to the remote repository
git push
```

> [!note] Note:
> When you have a content that you want to publish, run `./publish-content.sh`. 

2. Create `sync-content.sh` file one level outside the repo. The content of the file should copy from the Obsidian folder, and replace the content in this repo.
```sh
#!/bin/bash

# Define source and target directories

SOURCE_DIR="<folder-pathname>/public"

TARGET_DIR="<git-root-folder>/content"

# Use rsync to replace the contents of the target directory with the source directory

rsync -a --delete "$SOURCE_DIR/" "$TARGET_DIR"
```

## Hosting:
Resource: https://quartz.jzhao.xyz/hosting

