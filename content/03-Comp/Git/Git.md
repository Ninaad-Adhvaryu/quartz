- Git is for version control, track changes in a file over time.  
- Git, works locally.
## Commands

`git log` : to see all previous commits

`git commit -m "commit_name"` : to make a commit

> If you commit without -m option you will be put into a text editor. There are other examples too, like amending a commit and interactive rebase.

The **`git rebase`** and **`git merge`** commands are two ways of integrating changes from one Git branch into another.

### Merge

The **`git merge`** command allows users to merge changes from two different branches into one, usually the master branch. The command uses two commit pointers, the branch tips, and finds a common base commit between them. Then, Git creates a new merge commit that combines the changes.

Merging is useful when multiple developers have been working on the same codebase and have created multiple branches to implement different features or bug fixes. When the developers complete their work, they can merge their changes back into the master branch. Merging is also used when you want to create a new feature branch that includes changes from other branches.

The basic syntax for **`git merge`** is:

```
git merge <branch>
```

The command merges the changes from the specified **`<branch>`** into the branch you are currently on. Hence, **`git merge`** is often used with **`git checkout`** to [switch between branches](https://phoenixnap.com/kb/git-switch-branch)
If any conflicts arise during the merge, Git prompts you to resolve them before completing the merge.

![[Git-img-2311081815.png]]


#### Merging Advantages and Disadvantages

**Advantages**

- **Non-destructive**. Merging is a non-destructive operation in Git since it does not change the existing branches. It only adds an extra commit called merge commit.
- **Change integration**. Merging allows users to integrate changes from one branch into another. The integration is useful if multiple developers are working on different features that need to be merged into the master branch.
- **Multiple codebase versions**. Merging allows users to keep multiple codebase versions. This is useful if older code versions are necessary or if you need a separate branch for feature testing.
- **Change tracking**. Merging allows users to track the changes that have been made to the codebase. Tracking is useful for debugging or audits.
- **Conflict resolution**. Merging is a great conflict resolution mechanism that allows users to merge changes that multiple developers implemented on the same file.

**Disadvantages**

- **Merge conflicts**. One of the main disadvantages of **`git merge`** is the possibility of getting merge conflicts when making multiple changes to the same file. Sometimes, resolving such conflicts can be time-consuming and difficult.
- **Context loss**. When the changes from two branches are merged, some of the context of the changes may be lost. Thus, the codebase history and origin of some changes can be more difficult to trace.
- **Complexity**. The codebase complexity increases with the number of branches and merges, which increases maintenance difficulty and complicates the relationships between branches.
- **Dependencies**. Merging multiple branches into one can create dependencies between different parts of the codebase. This can further hinder testing and change deployment because changes in one part of the codebase can affect other parts.

### Rebase

The **`git rebase`** command integrates changes from one branch into a new base branch by replaying all the commits from the old branch into the new branch. The command rewrites the commit history of the original branch and creates a new branch by applying the same set of commits on top of the target branch.

When you rebase a branch, its base changes from one commit to another, making it appear as if it had been created from that commit. However, the branch is composed of completely new commits even though it looks the same.

Use **`git rebase`** when you want to incorporate changes from a feature branch into a main branch. For example, use the command when merging the changes from a feature branch into a development or master branch. Another great benefit of **`git rebase`** is that it can be used to clean up a messy commit history by combining or reordering commits logically.

The basic syntax for **`git rebase`** is:

```
git rebase <base>
```

The command rebases the current branch onto the specified **`<base>`**, which can be any commit reference (a commit ID, a branch name, a tag, or a relative reference to **`HEAD`**).

The diagram below shows a representation of **`git rebase`**:

![[Git-img-2311081815 1.png]]


#### Rebasing Advantages and Disadvantages

**Advantages**

- **Linear project history**. The major benefit of Git rebasing is a clean project history since the command eliminates unnecessary merge commits. The result is a perfectly linear project history, without any forks.
- **Simplified codebase**. The linear history makes it very easy to understand the codebase and track down the origin of specific changes.
- **Resolving merge conflicts.** The **`git rebase`** command applies changes from one branch on top of another. This means that merge conflicts are simplified, and changes are applied in a more orderly manner than in **`git merge`**.
- **Separate feature branches**. Rebasing can be used to separate feature branches on the master branch. Separating them makes it easier to manage multiple branches and keep them updated with the latest changes in the master branch.
- **Flexibility**. **`git rebase`** is more flexible than **`git merge`** in managing branches and committing changes because it allows users to reorder or modify commits, change commit messages, etc.

**Disadvantages**

- **Possible merge conflicts**. Rebasing a workflow may cause more frequent merge conflicts if there is a long-lived branch that has strayed far from the master branch. If the branch contains many new commits, they may conflict with the master branch. To avoid such issues, rebase your branches frequently against the master branch.
- **Lost commits**. Running **`git rebase`** in interactive mode with subcommands that remove commits from the branch can cause lost commits in the branch's immediate log. However, the commits can usually be restored by undoing the rebase with **`git reflog`**.
- **Lack of commit info**. After rebasing, you cannot see when the upstream changes were made and when they were incorporated into the feature branch.



## GitHub

- GitHub is a way to store the git repo online. 

Once you create a repo online, you can paste this into Git Bash to connect the two (I think). Example here for Obsidian vault.
```
git remote add origin https://github.com/Ninaad-Adhvaryu/obsidian-vault.git
git branch -M main
git push -u origin main
```


---

## Tail
###### Resources
https://phoenixnap.com/kb/git-rebase-vs-merge

###### See Also
[[Obsidian Git]]
