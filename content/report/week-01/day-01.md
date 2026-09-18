+++
title = "Day 01 - 17/08/2026 (on-site)"
weight = 1
+++


#### How to Use the Commands

##### 1. Initialize a Local Repository

First, I have a project containing only a `Project.md` file with the text "Hello world!".

I use `git init` to initialize a Git repository in the project directory. Git then creates a hidden `.git` directory to store metadata and version history.

![1789617421926](/report/week-01/image/day-01.vi/1789617421926.png)

##### 2. Create a GitHub Repository and Configure the Remote

Next, I sign in to GitHub and click **New** to create a repository.

![1789617470266](/report/week-01/image/day-01.vi/1789617470266.png)

I enter the repository name, set its visibility to public, and create it.

![1789617531589](/report/week-01/image/day-01.vi/1789617531589.png)

I use `git remote add origin` to connect the local repository to the GitHub repository. Then, I use `git remote -v` to verify the remote URL.

![1789617623214](/report/week-01/image/day-01.vi/1789617623214.png)

##### 3. Push Changes to GitHub

I run `git add` to move changes from the working directory to the staging area in preparation for a commit.

![1789617764959](/report/week-01/image/day-01.vi/1789617764959.png)

Next, I run `git commit` to save the staged changes in the Git history.

![1789617837157](/report/week-01/image/day-01.vi/1789617837157.png)

I use `git branch` to check the current branch.

![1789617885835](/report/week-01/image/day-01.vi/1789617885835.png)

The asterisk shows that I am currently on the `master` branch. I can rename it with `git branch -M <new-branch-name>`.

![1789617955822](/report/week-01/image/day-01.vi/1789617955822.png)

Finally, I push the changes to GitHub with `git push`.

![1789618035903](/report/week-01/image/day-01.vi/1789618035903.png)

![1789618057606](/report/week-01/image/day-01.vi/1789618057606.png)

##### 4. Clone the Repository as a Second User

I use `git clone` to download another copy of the project, simulating a second user.

![1789618189005](/report/week-01/image/day-01.vi/1789618189005.png)

The cloned directory contains both the source code and the Git history.

![1789618234642](/report/week-01/image/day-01.vi/1789618234642.png)

As the second user, I modify `Project.md`, commit the change, and push it to GitHub from the cloned directory.

![1789618846532](/report/week-01/image/day-01.vi/1789618846532.png)

![1789618421283](/report/week-01/image/day-01.vi/1789618421283.png)

##### 5. Retrieve Remote Changes with `fetch` and `pull`

GitHub now has a new commit that is not present in the first user's local repository.

I switch to the first user's directory and run `git fetch origin`.

![1789618505331](/report/week-01/image/day-01.vi/1789618505331.png)

`git fetch` downloads new metadata, branches, and commits from the remote repository, but it does not integrate them into the current branch.

![1789618699160](/report/week-01/image/day-01.vi/1789618699160.png)

![1789618902311](/report/week-01/image/day-01.vi/1789618902311.png)

Unlike `fetch`, `git pull` downloads remote changes and integrates them into the current branch.

![1789618941260](/report/week-01/image/day-01.vi/1789618941260.png)

![1789618956510](/report/week-01/image/day-01.vi/1789618956510.png)

`Project.md` is now up to date.

##### 6. Create and Switch Branches

I create a `feature-login` branch to develop the login feature independently from `main`.

![1789619033891](/report/week-01/image/day-01.vi/1789619033891.png)

The `feature-login` branch has been created, but the asterisk shows that I am still on `main`.

I then use `git checkout` to switch branches.

![1789619104186](/report/week-01/image/day-01.vi/1789619104186.png)

##### 7. Restore Uncommitted Changes

I intentionally add incorrect content to `Project.md`, then use Git to restore the file.

![1789619354173](/report/week-01/image/day-01.vi/1789619354173.png)

![1789619455955](/report/week-01/image/day-01.vi/1789619455955.png)

Although `git checkout` was traditionally used to switch branches, here I use it to restore `Project.md` to the version in the latest commit and discard its uncommitted changes.

##### 8. Update the Latest Commit with `commit --amend`

I create `README.md` and commit it as the first user.

![1789619757201](/report/week-01/image/day-01.vi/1789619757201.png)

Next, I modify `README.md` and amend the latest commit in the Git history.

![1789619906378](/report/week-01/image/day-01.vi/1789619906378.png)

##### 9. Unstage a File with `reset`

I now test the `git reset` command.

![1789620093843](/report/week-01/image/day-01.vi/1789620093843.png)

I use `git reset HEAD README.md` to remove the file from the staging area while keeping its changes in the working directory.

##### 10. Temporarily Store Changes with `stash`

Next, I test `git stash`. `README.md` contains changes that I am not ready to commit.

![1789620232022](/report/week-01/image/day-01.vi/1789620232022.png)

I use `git stash` to temporarily store the unfinished work and return the working directory to a clean state.

![1789620311688](/report/week-01/image/day-01.vi/1789620311688.png)

I then run `git stash pop` to restore the stashed changes.

![1789620438762](/report/week-01/image/day-01.vi/1789620438762.png)

##### 11. Reapply Commits with `rebase`

At this point, `feature-login` has changes to `README.md` and a new `login.txt` file that do not exist on `main`.

I switch to `main`, add the new feature, and commit it.

![1789620601395](/report/week-01/image/day-01.vi/1789620601395.png)

I switch back to `feature-login` and rebase it onto `main`.

![1789620706437](/report/week-01/image/day-01.vi/1789620706437.png)

The history of `feature-login` has now changed and includes the `feat: update new feature` commit.

Rebase creates a more linear commit history by replaying the commits from `feature-login` on top of `main`.

##### 12. Combine Branches with `merge`

After completing the login feature, I merge `feature-login` into `main`.

![1789620880413](/report/week-01/image/day-01.vi/1789620880413.png)

The changes from `feature-login` that were missing from `main`, including `README.md` and `login.txt`, are now available on `main`.

##### 13. Squash Commits with Interactive Rebase

I use the command shown below to create a new branch and switch to it.

![1789621099569](/report/week-01/image/day-01.vi/1789621099569.png)

![1789622885956](/report/week-01/image/day-01.vi/1789622885956.png)

I run `git rebase -i` to start an interactive rebase. Git opens an editor in which I can choose how each commit should be handled.

![1789622968826](/report/week-01/image/day-01.vi/1789622968826.png)

![1789622984259](/report/week-01/image/day-01.vi/1789622984259.png)

I change `pick` of commit 2 and 3 to `squash`, then use `:wq` to save and exit.

![1789623795093](/report/week-01/image/day-01.vi/1789623795093.png)

In the commit-message editor, I keep 1 commit message I want and remove other commits, then I save and exits.

![1789623905215](/report/week-01/image/day-01.vi/1789623905215.png)

The selected commits have now been combined into one commit.

##### 14. Apply a Specific Commit with `cherry-pick`

I create an `experimental` branch and commit a fix there.

![1789624270151](/report/week-01/image/day-01.vi/1789624270151.png)

![1789624436355](/report/week-01/image/day-01.vi/1789624436355.png)

After I run `git cherry-pick`, the fix commit from `experimental` is applied to `main`.
