- [Merge and Rebase](#merge-and-rebase)
  - [1. Git Merge](#1-git-merge)
    - [1.1 Merging](#11-merging)
    - [1.2 Basic Merge Conflicts](#12-basic-merge-conflicts)
  - [2. Git Rebase](#2-git-rebase)

# Merge and Rebase

## 1. Git Merge

### 1.1 Merging

- Basic Merging
  ![](../assets/06-basic-merge.png)

```
$ git checkout master
$ git merge hotfix
```

![Basic merge 2](../assets/06-basic-merge-2.png)

- Advanced Merging

![Basic merge 3](../assets/06-basic-merging-3.png)

- Three snapshots used in a typical merge

![Basic merge 4](../assets/06-basic-merging-4.png)

### 1.2 Basic Merge Conflicts

## 2. Git Rebase

![Rebase 1](../assets/06-basic-rebase-1.png)

```
$ git checkout experiment
$ git rebase master
```

![Rebase 1](../assets/06-basic-rebase-2.png)
