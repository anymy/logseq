---
title: Sync Script
---

## ## 'Last login: Fri Feb 19 17:28:06 on ttys003
manfredsteiner@Manfreds-MacBook-Pro ~ % cron                                   
cron: can't open or create /var/run/cron.pid: Permission denied
manfredsteiner@Manfreds-MacBook-Pro ~ % cd /usres
cd: no such file or directory: /usres
manfredsteiner@Manfreds-MacBook-Pro ~ % cd /Usres
cd: no such file or directory: /Usres
manfredsteiner@Manfreds-MacBook-Pro ~ % cd /Users
manfredsteiner@Manfreds-MacBook-Pro /Users % ls
Shared		manfredsteiner
manfredsteiner@Manfreds-MacBook-Pro /Users % cd manfredsteiner
manfredsteiner@Manfreds-MacBook-Pro ~ % ls
CmapToolsLogs	Documents	Library		Music		Public
Desktop		Downloads	Movies		Pictures	remnote
manfredsteiner@Manfreds-MacBook-Pro ~ % ls -al
total 72
drwxr-xr-x+ 28 manfredsteiner  staff    896 Feb 19 20:16 .
drwxr-xr-x   5 root            admin    160 Dec  8 07:42 ..
-r--------   1 manfredsteiner  staff      7 Jan  6 22:28 .CFUserTextEncoding
-rw-r--r--@  1 manfredsteiner  staff  12292 Feb 19 17:27 .DS_Store
drwxr-xr-x   2 manfredsteiner  staff     64 Feb 18 12:04 .InstallAnywhere
drwxr-xr-x   3 manfredsteiner  staff     96 Jan 14 11:03 .TheBrain
drwx------   2 manfredsteiner  staff     64 Feb 19 14:10 .Trash
drwx------   5 manfredsteiner  staff    160 Feb  1 22:03 .config
drwx------   3 manfredsteiner  staff     96 Jan  8 22:51 .cups
-rw-------   1 manfredsteiner  staff     58 Feb 19 16:55 .git-credentials
-rw-r--r--   1 manfredsteiner  staff     29 Feb 19 16:13 .gitconfig
-rw-r--r--   1 manfredsteiner  staff    206 Feb 11 15:47 .gtk-custom-papers
drwx------   3 manfredsteiner  staff     96 Jan 10 20:28 .local
drwxr-xr-x   8 manfredsteiner  staff    256 Feb  1 22:14 .npm
drwxr-xr-x   6 manfredsteiner  staff    192 Jan  7 01:58 .patched-sur
drwxr-xr-x   4 manfredsteiner  staff    128 Jan 14 12:21 .vscode
-rw-------   1 manfredsteiner  staff   3005 Feb 19 20:16 .zsh_history
drwx------  20 manfredsteiner  staff    640 Feb 19 20:16 .zsh_sessions
drwxr-xr-x   4 manfredsteiner  staff    128 Feb 18 12:07 CmapToolsLogs
drwx------@  6 manfredsteiner  staff    192 Feb 12 22:40 Desktop
drwx------@ 55 manfredsteiner  staff   1760 Feb 19 20:22 Documents
drwx------+ 53 manfredsteiner  staff   1696 Feb 19 16:00 Downloads
drwx------@ 71 manfredsteiner  staff   2272 Feb  2 00:17 Library
drwx------+  4 manfredsteiner  staff    128 Jan  7 09:35 Movies
drwx------+  4 manfredsteiner  staff    128 Jan  7 18:54 Music
drwx------+  5 manfredsteiner  staff    160 Feb  1 21:27 Pictures
drwxr-xr-x+  4 manfredsteiner  staff    128 Jan  6 21:26 Public
drwxr-xr-x   4 manfredsteiner  staff    128 Jan 18 14:23 remnote
manfredsteiner@Manfreds-MacBook-Pro ~ % cd .local
manfredsteiner@Manfreds-MacBook-Pro .local % ls
share
manfredsteiner@Manfreds-MacBook-Pro .local % ls -al
total 0
drwx------   3 manfredsteiner  staff   96 Jan 10 20:28 .
drwxr-xr-x+ 28 manfredsteiner  staff  896 Feb 19 20:16 ..
drwx------   3 manfredsteiner  staff   96 Feb 13 21:18 share
manfredsteiner@Manfreds-MacBook-Pro .local % mkdir bin
manfredsteiner@Manfreds-MacBook-Pro .local % cd bin
manfredsteiner@Manfreds-MacBook-Pro bin % touch logseq_sync.sh
manfredsteiner@Manfreds-MacBook-Pro bin % chmod +x logseq_sync.sh
manfredsteiner@Manfreds-MacBook-Pro bin % ls -al
total 0
drwxr-xr-x  3 manfredsteiner  staff   96 Feb 19 20:51 .
drwx------  4 manfredsteiner  staff  128 Feb 19 20:50 ..
-rwxr-xr-x  1 manfredsteiner  staff    0 Feb 19 20:51 logseq_sync.sh
manfredsteiner@Manfreds-MacBook-Pro bin % vi logseq_sync.sh

[No write since last change]
21:00  up 17 days, 9 hrs, 3 users, load averages: 2.88 3.27 3.34
USER     TTY      FROM              LOGIN@  IDLE WHAT
manfredsteiner console  -                02Feb21 17days -
manfredsteiner s000     -                20:16       - w
manfredsteiner s001     -                20:58       - -zsh

Press ENTER or type command to continue
manfredsteiner@Manfreds-MacBook-Pro bin % ls
logseq_sync.sh
manfredsteiner@Manfreds-MacBook-Pro bin % ls -al
total 8
drwxr-xr-x  3 manfredsteiner  staff   96 Feb 19 21:00 .
drwx------  4 manfredsteiner  staff  128 Feb 19 20:50 ..
-rwxr-xr-x  1 manfredsteiner  staff  297 Feb 19 21:00 logseq_sync.sh
manfredsteiner@Manfreds-MacBook-Pro bin % vi logseq_sync.sh
manfredsteiner@Manfreds-MacBook-Pro bin % ./logseq_sync.sh
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.

    git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

    git branch --set-upstream-to=origin/<branch> master

There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.

    git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

    git branch --set-upstream-to=origin/<branch> master

fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin master

manfredsteiner@Manfreds-MacBook-Pro bin % ls -al           
total 8
drwxr-xr-x  3 manfredsteiner  staff   96 Feb 19 21:01 .
drwx------  4 manfredsteiner  staff  128 Feb 19 20:50 ..
-rwxr-xr-x  1 manfredsteiner  staff  297 Feb 19 21:00 logseq_sync.sh
manfredsteiner@Manfreds-MacBook-Pro bin % vi logseq_sync.sh
manfredsteiner@Manfreds-MacBook-Pro bin % ./logseq_sync.sh 
total 16
drwxr-xr-x@  7 manfredsteiner  staff   224 Feb 19 21:01 .
drwx------@ 55 manfredsteiner  staff  1760 Feb 19 21:01 ..
-rw-r--r--@  1 manfredsteiner  staff  6148 Feb 19 17:27 .DS_Store
drwxr-xr-x@ 13 manfredsteiner  staff   416 Feb 19 21:01 .git
drwxr-xr-x@  7 manfredsteiner  staff   224 Feb 19 20:22 journals
drwxr-xr-x@  4 manfredsteiner  staff   128 Feb 19 17:20 logseq
drwxr-xr-x@  4 manfredsteiner  staff   128 Feb 19 17:20 pages
There is no tracking information for the current branch.
Please specify which branch you want to merge with.
See git-pull(1) for details.

    git pull <remote> <branch>

If you wish to set tracking information for this branch you can do so with:

    git branch --set-upstream-to=origin/<branch> master

manfredsteiner@Manfreds-MacBook-Pro bin % vi logseq_sync.sh
manfredsteiner@Manfreds-MacBook-Pro bin % ./logseq_sync.sh 
total 16
drwxr-xr-x@  7 manfredsteiner  staff   224 Feb 19 21:01 .
drwx------@ 55 manfredsteiner  staff  1760 Feb 19 21:01 ..
-rw-r--r--@  1 manfredsteiner  staff  6148 Feb 19 17:27 .DS_Store
drwxr-xr-x@ 13 manfredsteiner  staff   416 Feb 19 21:01 .git
drwxr-xr-x@  7 manfredsteiner  staff   224 Feb 19 20:22 journals
drwxr-xr-x@  4 manfredsteiner  staff   128 Feb 19 17:20 logseq
drwxr-xr-x@  4 manfredsteiner  staff   128 Feb 19 17:20 pages
From https://github.com/anymy/logseq
 * branch            main       -> FETCH_HEAD
Already up to date.
manfredsteiner@Manfreds-MacBook-Pro bin % vi logseq_sync.sh
manfredsteiner@Manfreds-MacBook-Pro bin % ./logseq_sync.sh 
total 16
drwxr-xr-x@  7 manfredsteiner  staff   224 Feb 19 21:12 .
drwx------@ 55 manfredsteiner  staff  1760 Feb 19 21:12 ..
-rw-r--r--@  1 manfredsteiner  staff  6148 Feb 19 17:27 .DS_Store
drwxr-xr-x@ 14 manfredsteiner  staff   448 Feb 19 21:06 .git
drwxr-xr-x@  7 manfredsteiner  staff   224 Feb 19 21:12 journals
drwxr-xr-x@  4 manfredsteiner  staff   128 Feb 19 17:20 logseq
drwxr-xr-x@  4 manfredsteiner  staff   128 Feb 19 17:20 pages
From https://github.com/anymy/logseq
 * branch            main       -> FETCH_HEAD
Already up to date.
From https://github.com/anymy/logseq
 * branch            main       -> FETCH_HEAD
Already up to date.
fatal: The current branch master has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin master

manfredsteiner@Manfreds-MacBook-Pro bin % vi logseq_sync.sh
manfredsteiner@Manfreds-MacBook-Pro bin % ./logseq_sync.sh 
total 16
drwxr-xr-x@  7 manfredsteiner  staff   224 Feb 19 21:12 .
drwx------@ 55 manfredsteiner  staff  1760 Feb 19 21:12 ..
-rw-r--r--@  1 manfredsteiner  staff  6148 Feb 19 17:27 .DS_Store
drwxr-xr-x@ 14 manfredsteiner  staff   448 Feb 19 21:12 .git
drwxr-xr-x@  7 manfredsteiner  staff   224 Feb 19 21:12 journals
drwxr-xr-x@  4 manfredsteiner  staff   128 Feb 19 17:20 logseq
drwxr-xr-x@  4 manfredsteiner  staff   128 Feb 19 17:20 pages
From https://github.com/anymy/logseq
 * branch            main       -> FETCH_HEAD
Already up to date.
manfredsteiner@Manfreds-MacBook-Pro bin % ./logseq_sync.sh
total 16
drwxr-xr-x@  7 manfredsteiner  staff   224 Feb 19 21:26 .
drwx------@ 55 manfredsteiner  staff  1760 Feb 19 21:26 ..
-rw-r--r--@  1 manfredsteiner  staff  6148 Feb 19 17:27 .DS_Store
drwxr-xr-x@ 14 manfredsteiner  staff   448 Feb 19 21:23 .git
drwxr-xr-x@  7 manfredsteiner  staff   224 Feb 19 21:26 journals
drwxr-xr-x@  4 manfredsteiner  staff   128 Feb 19 17:20 logseq
drwxr-xr-x@  4 manfredsteiner  staff   128 Feb 19 17:20 pages
From https://github.com/anymy/logseq
 * branch            main       -> FETCH_HEAD
Already up to date.
From https://github.com/anymy/logseq
 * branch            main       -> FETCH_HEAD
Already up to date.
Branch 'main' set up to track remote branch 'main' from 'origin'.
manfredsteiner@Manfreds-MacBook-Pro bin % crontab -e
crontab: no crontab for manfredsteiner - using an empty one
crontab: "/usr/bin/vi" exited with status 1
manfredsteiner@Manfreds-MacBook-Pro bin % crontab -e
crontab: no crontab for manfredsteiner - using an empty one
crontab: installing new crontab
"/tmp/crontab.hcMaTC7T7c":1: bad minute
crontab: errors in crontab file, can't install
Do you want to retry the same edit? yes     
crontab: installing new crontab
manfredsteiner@Manfreds-MacBook-Pro bin % crontab
^[Q
^C
manfredsteiner@Manfreds-MacBook-Pro bin % crontab -e
crontab: installing new crontab
manfredsteiner@Manfreds-MacBook-Pro bin % crontab -e
crontab: no changes made to crontab
manfredsteiner@Manfreds-MacBook-Pro bin % ls
logseq_sync.sh
manfredsteiner@Manfreds-MacBook-Pro bin % vi logseq_sync.sh


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
#
git add .
#
git commit -q -m "Last Sync: $(date +"%Y-%m-%d %H:%M:%S")"
# git push --set-upstream origin main -q'
