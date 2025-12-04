# Git Notes

## Git
Git is a Version Control System. It is a tool that helps to track changes in code.

## Untracked Files
Files that are not tracked by git and are new.

## Staged
Files that are ready to be commit.

## Pull Request
Request to merge code from 1 branch to another. It can include reviewer to approve the code.

## Merge Conflict
An event when github is unable to resolve differences in code.

## Fork
Fork is a new repository that shares code and visibility settings with the original upstream repository. It is a rough copy of repository.

## Configure Commands
```
git config --global user.name "Name"
git config --global user.email "Email"
git config --list
```

## Initialize Commands
* `git clone <link>` Clone a repository on the local machine.
* `git init` Create new git repository.
* `git remote add origin <link>` Add remote orgin to new repository.
* `git remote -v` Check remote.

## Branch Commands
* `git branch` Check branch.
* `git branch -M <name>` Change branch name.
* `git checkout <branch>` Change branch.
* `git branch -b <name>` Create new branch.
* `git branch -d <name>` Delete a local branch. Cannot delete current branch.
* `git push -d origin <name>` Delete remote branch.

## Code Push Commands
* `git status` Display state of the code.
* `git add <files>` Add new or changed files in your working directory to the Git staging area.
* `git commit -m "Message"` It is the record of change.
* `git push origin <branch>` Upload local repository content to remote repository. Use -u to set origin branch as default so we can only use git push.

## Merge Commands
* `git diff <branch>` Difference of current branch with the given branch.
* `git merge <branch>` Merge branch in current branch.
* `git pull origin <branch>` Get code from remote branch.

## Undo Commands
* `git reset <file>` Unstage a staged file. Use --hard to also remove unstaged changes and have a clean repository.
* `git reset` Unstage all staged files.
* `git reset HEAD~<count>` Go back in commits stack count times. Like if you commited something which you want to remove then use git reset HEAD~1 to undo commit. You will still have the changes as unstaged files.
* `git log` Check previous commits.
* `git reset <commit hash>` Go back to a specific commit.

## GitFlow Branches
* `main`
* `develop`
* `feature/name`
* `test/name`
* `docs/name`
* `release/1.0.0`
* `bug/name`
* `hotfix/name`

## GitFlow
* We create `develop` from `main` branch.
* Now we create feature/test/docs branch from `develop`.
* After completing feature we merge it to `develop`.
* Then we create `release` branch from `develop`.
* Then we create `bug` branch from `release` and finally that final `release` is merged to `develop` and `main`.
* We create `hotfix` from `main` and fix the bug and then merge it with `main` and `develop`.

## Readme File Formatting
* \*\***Bold Text**\*\*
* \**Italic Text*\*
* \~~Cancelled Text~\~
* `<sub>`<sub>Subscript</sub>`</sub>`
* `<ins>`<ins>Underline</ins>`</ins>`
* > \> This is a quote.
* Here is the code \``git status`\`
* \`\`\```` this is a code block ```\`\`\`
* This is a link `[Text to show](https://pagelink.com)`
* \* This is a bullet point.
