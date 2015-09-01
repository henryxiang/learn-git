Working with a Local Repository
-------------------------------

### Initial setup

`git config --global user.name "Henry Xiang"`

`git config --global user.email "henryxiang@gmail.com"`

`git config --list`

### Create a new Git repo.

`git init git-demo`

### Look into a Git repo.

`ls -a`

`tree .git

### Create a new file.

`echo "Hello Git" >> hello.txt`

### Add the file to index (staging area) and then check the object cache.

`git add .`

`git status`

`tree .git/objects`

### Recreate SHA-1 hash with shasum and git hash-object command.

`echo -e "blob 10\0Hello Git" | shasum`

`echo "Hello Git" | git hash-object --stdin -w`

### Commit the changes and check the object cache again.

`git commit -m "first commit"`

`tree. git/objects`

### Inspect Git objects with git cat-file command.

`git cat-file -t 2f092e`

`git cat-file -t 9f4d96`

`git cat-file -t ba97de`

`git cat-file -p ba97de`

`git cat-file -p 2f092e`

`git cat-file -p 9f4d96`

### The first commit also create a branch named 'master'.

`git branch`

### Branch is just a "pointer" to a commit.

`git cat-file -t master`

`git rev-parse master`

`git cat-file -p master`

### Add more changes and commit.

`echo "Git is fun" >> hello.txt && git add . && git commit -m "added some fun"`

### Git log

`git log`

`git log -1`

`git log HEAD~2`

`git log --after="5 minutes ago" --before="1 minutes ago"`

`git log --grep="first"`

`git log --oneline --decorate --graph --all`

`git lg`

### Make a new "feature" branch.

`git branch feature`

`git checkout -b feature`

`git lg`

### Check out the feature branch and commit a change

`git checkout feature`

`echo "feature 1" >> hello.txt && git add . && git commit -m "added feature 1"

`git lg`

### Merging and resolving merge conflict

`git branch hotfix master`

`git checkout hotfix`

`echo "hotfix 1" >> hello.txt && git add . && git commit -m "added hotfix 1"`

`git lg`

`git checkout master`

`git merge hotfix`

`git lg`

`git merge feature`

`git mergetool`

`git commit -m "merged in feature branch; resolved conflicts"`

`git lg`

`git cat-file -p master`

### Remove branches

`git branch -d feature`

`git branch -d hotfix`

