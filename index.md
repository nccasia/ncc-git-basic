# ncc-git-basic

NCC Git Basic là một series về git cơ bản, trong series này mình sẽ cố gắng chắt lọc và giới thiệu đến các bạn những kiến thức cơ bản nhất, hay được sử dụng trong thực tế nhất. Giúp các bạn tránh lan man, học dàn trải khi tiếp cận git.

[0. Git flow (step by step without git knowledge)](#git-flow)

[1. What is git?](./book/01-what-is-git)

[2. Getting Started: `git clone || git init`](./book/02-get-started)

[3. The lifecycle of the status of your files: `git status` - `git add` - `git reset or git restore` - `git commit`](./book/03-lifecycle-of-the-status)

[3.1 Stashing: `git stash`](./book/03-lifecycle-of-the-status#8-git-stash)

[4. Working with Remotes: `git remote` - `git pull` - `git push` - `git fetch`](./book/04-working-with-remotes)

[4.1. HTTPS and SSH](./book/04-working-with-remote)

[5. Git Branching: `git branch` - `git checkout`](./book/05-git-branching)

[6. Git Branching(2) - Merging and Rebasing: `git merge` - `git rebase`](./book/06-git-branching-2-merging-and-rebasing.d)

[6.1. Resolve Conflict](./book/06-git-branching-2-merging-and-rebasing/#12-basic-merge-conflicts)

[7. Git Branching(3) - Branch Management and Commit history: `git branch` - `git log`](./book/07-git-branching-branch-management-and-commit-history)

[8. Git Advanced - Cherry Pick](#)

[9. Git Advanced - `rebase -i` and `commit --amend`](#)

## Git flow

### 1. Work on new brand

Check out from master or dev branch: `git checkout -b your-new-branch`

### 2. After finished your work. Add your change to staged and commit it

`git add .` or `git add your-file-name`

`git commit -m "Commit's message"`

### 3. After commit, merge the latest code from remote branch

#### 3.1. The first way - Use MERGE

- Pull the latest code: `git pull origin dev` or `git pull origin master`
- Fix the conflict if you have and commit it

#### 3.2. The second way - Use REBASE

- Checkout to master (or dev): `git checkout master`
- Pull the latest code: `git pull origin master`
- Checkout back to your new branch: `git checkout your-new-branch`
- Rebase master: `git rebase master`
- Fix the conflict if you have and then add it to staged `git add .`
- After that, use `git rebase --continue`

### 4. Push your branch

`git push origin your-new-branch`

### 5. Create Merge Request on remote repository

**References**

1. https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F
2. https://www.freecodecamp.org/news/what-is-git-and-how-to-use-it-c341b049ae61/
3. https://topdev.vn/blog/git-la-gi/
4. https://www.atlassian.com/git/tutorials/git-ssh
5. https://viblo.asia/p/git-dung-https-hay-ssh-eW65Gm9jZDO
6. https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys
