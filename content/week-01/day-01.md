+++
title = "Day 01 - 15/06/2026"
weight = 1
+++

## Topics Learned

### Git

#### Common Commands

| Command            | Meaning                                        |
| ------------------ | ---------------------------------------------- |
| git init           | Create a new Git repository                    |
| git remote         | Manage connections to remote repositories      |
| git clone          | Copy a remote repository to the local machine  |
| git fetch          | Download remote changes without merging them   |
| git pull           | Download and merge remote changes              |
| git status         | Show the current repository state              |
| git branch         | List, create, or delete branches               |
| git switch         | Move to another branch                         |
| git checkout       | Switch branches or restore files               |
| git add            | Stage changes for the next commit              |
| git commit         | Save staged changes to the repository history  |
| git commit --amend | Update the latest commit                       |
| git push           | Upload local commits to a remote repository    |
| git reset          | Unstage changes or move commit history         |
| git rebase         | Reapply commits on top of another branch       |
| git rebase -i      | Edit, squash, or reorder commits interactively |
| git stash          | Temporarily save uncommitted work              |
| git stash pop      | Restore the latest stashed work                |
| git merge          | Combine changes from another branch            |
| git cherry-pick    | Apply a specific commit to the current branch  |

#### How to Use the Commands

##### 1. Initialize a Local Repository

First, I have a project containing only a `Project.md` file with the text "Hello world!".

I use `git init` to initialize a Git repository in the project directory. Git then creates a hidden `.git` directory to store metadata and version history.

![1789617421926](/week-01/image/day-01.vi/1789617421926.png)

##### 2. Create a GitHub Repository and Configure the Remote

Next, I sign in to GitHub and click **New** to create a repository.

![1789617470266](/week-01/image/day-01.vi/1789617470266.png)

I enter the repository name, set its visibility to public, and create it.

![1789617531589](/week-01/image/day-01.vi/1789617531589.png)

I use `git remote add origin` to connect the local repository to the GitHub repository. Then, I use `git remote -v` to verify the remote URL.

![1789617623214](/week-01/image/day-01.vi/1789617623214.png)

##### 3. Push Changes to GitHub

I run `git add` to move changes from the working directory to the staging area in preparation for a commit.

![1789617764959](/week-01/image/day-01.vi/1789617764959.png)

Next, I run `git commit` to save the staged changes in the Git history.

![1789617837157](/week-01/image/day-01.vi/1789617837157.png)

I use `git branch` to check the current branch.

![1789617885835](/week-01/image/day-01.vi/1789617885835.png)

The asterisk shows that I am currently on the `master` branch. I can rename it with `git branch -M <new-branch-name>`.

![1789617955822](/week-01/image/day-01.vi/1789617955822.png)

Finally, I push the changes to GitHub with `git push`.

![1789618035903](/week-01/image/day-01.vi/1789618035903.png)

![1789618057606](/week-01/image/day-01.vi/1789618057606.png)

##### 4. Clone the Repository as a Second User

I use `git clone` to download another copy of the project, simulating a second user.

![1789618189005](/week-01/image/day-01.vi/1789618189005.png)

The cloned directory contains both the source code and the Git history.

![1789618234642](/week-01/image/day-01.vi/1789618234642.png)

As the second user, I modify `Project.md`, commit the change, and push it to GitHub from the cloned directory.

![1789618846532](/week-01/image/day-01.vi/1789618846532.png)

![1789618421283](/week-01/image/day-01.vi/1789618421283.png)

##### 5. Retrieve Remote Changes with `fetch` and `pull`

GitHub now has a new commit that is not present in the first user's local repository.

I switch to the first user's directory and run `git fetch origin`.

![1789618505331](/week-01/image/day-01.vi/1789618505331.png)

`git fetch` downloads new metadata, branches, and commits from the remote repository, but it does not integrate them into the current branch.

![1789618699160](/week-01/image/day-01.vi/1789618699160.png)

![1789618902311](/week-01/image/day-01.vi/1789618902311.png)

Unlike `fetch`, `git pull` downloads remote changes and integrates them into the current branch.

![1789618941260](/week-01/image/day-01.vi/1789618941260.png)

![1789618956510](/week-01/image/day-01.vi/1789618956510.png)

`Project.md` is now up to date.

##### 6. Create and Switch Branches

I create a `feature-login` branch to develop the login feature independently from `main`.

![1789619033891](/week-01/image/day-01.vi/1789619033891.png)

The `feature-login` branch has been created, but the asterisk shows that I am still on `main`.

I then use `git checkout` to switch branches.

![1789619104186](/week-01/image/day-01.vi/1789619104186.png)

##### 7. Restore Uncommitted Changes

I intentionally add incorrect content to `Project.md`, then use Git to restore the file.

![1789619354173](/week-01/image/day-01.vi/1789619354173.png)

![1789619455955](/week-01/image/day-01.vi/1789619455955.png)

Although `git checkout` was traditionally used to switch branches, here I use it to restore `Project.md` to the version in the latest commit and discard its uncommitted changes.

##### 8. Update the Latest Commit with `commit --amend`

I create `README.md` and commit it as the first user.

![1789619757201](/week-01/image/day-01.vi/1789619757201.png)

Next, I modify `README.md` and amend the latest commit in the Git history.

![1789619906378](/week-01/image/day-01.vi/1789619906378.png)

##### 9. Unstage a File with `reset`

I now test the `git reset` command.

![1789620093843](/week-01/image/day-01.vi/1789620093843.png)

I use `git reset HEAD README.md` to remove the file from the staging area while keeping its changes in the working directory.

##### 10. Temporarily Store Changes with `stash`

Next, I test `git stash`. `README.md` contains changes that I am not ready to commit.

![1789620232022](/week-01/image/day-01.vi/1789620232022.png)

I use `git stash` to temporarily store the unfinished work and return the working directory to a clean state.

![1789620311688](/week-01/image/day-01.vi/1789620311688.png)

I then run `git stash pop` to restore the stashed changes.

![1789620438762](/week-01/image/day-01.vi/1789620438762.png)

##### 11. Reapply Commits with `rebase`

At this point, `feature-login` has changes to `README.md` and a new `login.txt` file that do not exist on `main`.

I switch to `main`, add the new feature, and commit it.

![1789620601395](/week-01/image/day-01.vi/1789620601395.png)

I switch back to `feature-login` and rebase it onto `main`.

![1789620706437](/week-01/image/day-01.vi/1789620706437.png)

The history of `feature-login` has now changed and includes the `feat: update new feature` commit.

Rebase creates a more linear commit history by replaying the commits from `feature-login` on top of `main`.

##### 12. Combine Branches with `merge`

After completing the login feature, I merge `feature-login` into `main`.

![1789620880413](/week-01/image/day-01.vi/1789620880413.png)

The changes from `feature-login` that were missing from `main`, including `README.md` and `login.txt`, are now available on `main`.

##### 13. Squash Commits with Interactive Rebase

I use the command shown below to create a new branch and switch to it.

![1789621099569](/week-01/image/day-01.vi/1789621099569.png)

![1789622885956](/week-01/image/day-01.vi/1789622885956.png)

I run `git rebase -i` to start an interactive rebase. Git opens an editor in which I can choose how each commit should be handled.

![1789622968826](/week-01/image/day-01.vi/1789622968826.png)

![1789622984259](/week-01/image/day-01.vi/1789622984259.png)

I change `pick` to `squash`, then use `:wq` to save and exit.

![1789623795093](/week-01/image/day-01.vi/1789623795093.png)

In the commit-message editor, I keep 1 commit message I want and remove other commits, then I save and exits.

![1789623905215](/week-01/image/day-01.vi/1789623905215.png)

The selected commits have now been combined into one commit.

##### 14. Apply a Specific Commit with `cherry-pick`

I create an `experimental` branch and commit a fix there.

![1789624270151](/week-01/image/day-01.vi/1789624270151.png)

![1789624436355](/week-01/image/day-01.vi/1789624436355.png)

After I run `git cherry-pick`, the fix commit from `experimental` is applied to `main`.

#### Merge Conflict Handling

| Situation                        | Solution in Code Source Control                                     |
| -------------------------------- | ------------------------------------------------------------------- |
| Keep changes from both branches  | Open the file, edit the conflict manually, then mark it as resolved |
| Keep the current branch version  | Use `Accept Current Change` in the conflict editor                  |
| Keep the incoming branch version | Use `Accept Incoming Change` in the conflict editor                 |
| Cancel the merge                 | Open Source Control, use the `...` menu, then choose `Abort Merge`  |
| Resolve conflicts manually       | Review the marked conflict blocks and keep the correct final code   |

### TypeScript

#### Interface vs Type

- Use `interface` when the main goal is to describe object structure and support inheritance.
- Use `type` when the shape is more complex, such as a union, tuple, primitive alias, or function type.
- Both are valid for object modeling, so choose the one that fits the use case and team convention.

#### Union Type

- A union type allows a value to have more than one possible type.
- It uses the `|` operator.

#### Omit Utility Type

- `Omit` creates a new type by removing one or more properties from an existing type.
- It is useful when reusing a model but hiding fields that are not needed.

#### Extends

- `extends` lets an interface inherit properties from another interface.
- It reduces duplication and keeps related types consistent.

---

### ESLint

#### Purpose of ESLint

- ESLint is a static analysis tool for JavaScript and TypeScript.
- It helps detect errors and warnings before runtime.
- It keeps code aligned with project conventions.

#### Common Errors and Warnings

- `no-unused-vars`: a variable is declared but not used.
- `no-undef`: a variable is used before it is defined.
- `react-hooks/rules-of-hooks`: React Hooks are used in the wrong place.
- `react-hooks/exhaustive-deps`: a `useEffect` dependency is missing.
- `no-magic-numbers`: a hard-coded number is used without clear meaning.

## Lessons Learned

- Avoid **"magic numbers"**.
- Do not commit `node_modules`.
- Understand the difference between merge and rebase.
- Use `git add <file>` instead of `git add .` when possible.

### Key Principles

- Organize `src/` by feature or by file type.
- Keep configuration files at the project root.
- Always add `node_modules/` and `dist/` to `.gitignore`.
- Use clear and descriptive folder names.
- Group related files together for easier navigation.
