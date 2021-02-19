---
title: Sync Script
---

## ```
LOGSEQ_PATH="/Users/manfredsteiner/Documents/LogSeq"
LOGSEQ_REPO="https://github.com/anymy/logseq"

cd "$LOGSEQ_PATH"

ls -al

git pull "$LOGSEQ_REPO" main

CHANGES_EXIST="$(git status --porcelain | wc -l)"

if [ "$CHANGES_EXIST" -eq 0 ]; then
        exit 0
fi

git pull "$LOGSEQ_REPO" main
## git add .
#
git commit -q -m "Last Sync: $(date +"%Y-%m-%d %H:%M:%S")"
# git push --set-upstream origin main -q```
