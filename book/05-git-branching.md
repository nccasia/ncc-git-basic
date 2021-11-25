- [Git branching](#git-branching)
  - [1. Overview](#1-overview)
  - [2. Create branch](#2-create-branch)
  - [3. Switching Branches](#3-switching-branches)

# Git branching

## 1. Overview

- Commits and Parents
  ![Commits and Parents](../assets/05-commits-and-parents.png)

- Branch and History
  ![Branch and History](../assets/05-branch-and-history.png)

## 2. Create branch

```
$ git branch testing
```

Two branches pointing into the same series of commits
![Two Branch](../assets/05-two-branches.png)

## 3. Switching Branches

```
$ git checkout testing
```

![](../assets/05-head-to-testing.png)

Checkout master

![](../assets/05-checkout-master.png)

New commit on master

![](../assets/05-advance-master.png)

```
$ git log --oneline --graph --all
```

```
$ git checkout -b testing-2
```
