
Eliminate need of a Password every git push: 
- (**Enable Credential Helper**: Configure Git to use the credential helper to cache your credentials:) 
```
git config --global credential.helper cache
```

# Github concepts

How do you recognize a directory in your workspace is a git repository?
- .git (a directory) is created within the directory.

## Git states:
- workspace
- Index (When you "stage" a file)
- Local repository (When you "commit" a file)
- Remote repository (When you "push" a file)

![[git_data_transport_commands.png]]

git push, SSH setup
- Why do we use SSH? To  generate an encrypted key that can help you connect you local repo to the remote repo (Hosted by another computer)
- Steps:
	- ssh-keygen -t  rsa -b 4096 -C "{email you used for you git account}"
		- -t: Specifies the type of encryption
		- -b: The strength of encryption 
		- -C: Github email address
		- Result (Once it is ran): It will create a public and private {type of encrytion} key pair that is stored in a .ssh file in your local machine, where you use as workspace, and ask to give a name to both keys, and give them both another layer of optional password.
			- Public key ({keyname}.pub): This key can be shared with others. It is used to encrypt/ decrypt data. Data encrypted with public key can be decrypted by private key.
			- Private key ({keyname}): This key can only stay on your local machine. It is used to encrypt/ decrypt data. Data encrypted with private key can be decrypted by public key. But private key is specifically responsible in generating a public key, not the other way around.
	- Copy your Public key
	- In Github, go to settings > SSH and CPG keys > New SSH Keys (To add newly generated SSH key to you list of existing SSH keys) > Give you key a name, and paste your "Public key". (Now remote git knows the key you have generated)
	- We have to let our workspace know about the key that was generated. Follow the steps: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent (This is a crucial step, with some complex commands)

"Merging"
- The process of combining code from two branches.
![[git_merging.png]]

## Git ignore
- To ignore files/ directories when committing to local repo/ pushing to remote repo.
Git ignore a directory (recursively) 
1) Create a `touch .gitignore` file
2) Add the line `/{directory_name}/` in the file - directory you want to ignore during commits, and remote push. 
	- ***(a forward slash (/) at the beginning of the directory name to indicate that it should be ignored recursively.)***
- Example:
	- `dir1/`
	- `.hidden_dir/`

## Removing files from git states
Removing tracked files
- If you want to remove a file that is already being tracked by Git, you can add the `--cached` option to remove the file from the repository but keep it in your working directory. This is useful when you want to stop tracking the file but retain your local copy:
> `--cached` flag: Crucial for specifying that you only want to remove the file from the index, not from your local filesystem.
``` bash
# Remove tracked files
git rm --cached path/to/your/file
```

``` bash
# Remove tracked directory 
git rm -r --cached path/to/your/dir
```


------

# Git commands
- `git init`
	- Creates a local repository, with index area which is a .git directory in your workspace.
	 
- `git remote {optional: flag} {optional: git command} {optional: url}`
	(So lets say you created a local repository, how do you push it to a remote repository. This problem often arise when you git init - which creates a local repo, but the remote repo has no idea that you created one, or which local repo to connect to the remote repo to.)
	- If you do not have a remote repository is created (Remote repository != Git. Git has many remote repositories): 
		- Go to github to create a new remote repo
	- If you already created a remote repository (e.g., using git hub), and wish to connect it to your local repository you have just "init":
		- use git remote commands (E.g., "git remote add origin {git_url_copied_from_github}")
	- flag: 
		- -v:  Shows the remote repository connected to this repo.
- `git status`
	- Shows all files that were updated, created, or deleted, BUT have not been saved in a commit.
	- Status:
		- "Staged"
		- "Unstaged"
	- Each item:
		- "modified" (git knows it is changed, but change is not committed) 
			- E.g., Where a file can be "unstaged and modified"
		- "untracked" (git has no idea about this file)

`git diff`
Shows the difference between the working directory (modified but not staged changes) and the last commit. 
- (aka. showing what is modified in the file, which has caused it to change to a "modified" state when using `git status`)
```
git diff path/to/file
```

Reading git diff --- [YT, How to Read Git Diff Output](https://www.youtube.com/watch?v=OWS_ETgpLFQ)

When comparing two files, `diff` finds sequences of lines common to both files, interspersed with groups of differing lines called _hunks_.
- Example of 1 "*hunk*": 
```
@@ -1, 12 +1, 16 @@
# 
# 
# 
- # ABC
- # DEF
# xxx
# 
+ # GHI
+ # JKL
```
> We show 1) a hunk, specified with numbered lines; 2) common lines; 3) contents from file A; 4) contents from file B.
-   `@@ -{start-line}{number-of-lines} +{start-line}{number-of-lines} @@`: lines of interest.
- `# {content}`: common lines
- `- # {content}`: Differed lines in File A (i.e., if we concatenate only the the common lines + differed lines in file A, we get File A.)
- `+ # {content}`: Differed lines in File B (i.e., if we concatenate only the the common lines + differed lines in file B, we get File B.)




- `git add {target}`
	- "Staging" operation: Asks git to "add" all "untracked" files IN the local workspace by "staging" it TO "the Index".
	- Target:
		- --all
		- .
		- {filename}
		
- UNDO STAGING:  `git reset `
	- `git reset {optional: name_of_the_file}`  - undos staging for only the named files. 
	- Unstage all staged files (after using `git add`) from the Index 
	- {optional: name_of_the_file}
		- unstage the specified file from the Index
	- When you type git status again, you will see that the files are "unstaged and modified"

- `git commit -{flag} {commit message} {optional: {description of the commit message}}`
	- -m {commit message}: Commits the "staged code" at index to the local repository. (Note that code has to be staged and recognized by the Index before it can be committed.)
	- -am {commit message}: Commits the "staged code" at index to the local repository. (Note that code has to be staged and recognized by the Index before it can be committed.(This can only be used on "tracked" file/ files that was staged before,and are currently just "modifiying")

## Git branching
- Resources:
	- [Youtube video: Git branching and merging - Detailed tutorial](https://www.youtube.com/watch?v=Q1kHG842HoI)
A copy of the main/ master branch version at the time when the branch is created.

"Branching"
- A branch is like a buffer for code. Changes to specific branches does not affect other branches.
- Keep in mind in larger code bases, there could be nested branches. It acts as a buffer before reaching the master branch. Kind of like how multiple bosses has to review the code before the final CEO (master) can approve for production. People often use branch names like: dev branch, staging branch for that purpose, where these branch never gets deleted, but acts as a place for other pulled request branches to reside.
- Type of branches:
	- Master branch (The main implementation)
	- Feature branch
		- ![[git_feature_branching.png]]
	- Hot fix branch
		- ![[git_hot_fix_branching.png]]
	- Staging branch
	- Dev branch
- State of branches:
	- "Open" (A branch that has not been merged)
	- "Merged" (A branch that has already been merged)

- `git log {optional: options}`
	- Shows commit logs of your ENTIRE REMOTE REPO currently pulled into your LOCAL REPO. 
		- When you fetch or pull changes from a remote repository, those changes are copied to your local repository, so you have the entire commit history of the remote repository in your local repository.
	- Labels:
		- `({branch_name})`: Indicates the commit made to that specific branch.
		- `(HEAD -> {branch_name})`: Indicates the branch which you are in. (so you can easily distinct the commits made in different branches in your ENTIRE REPO).
	- Meaning of edges in `--graph`:
		- An edge connecting sequentially/ linearly indicates the changes made in that branch.
		- An edge deviating from a single commit node (regardless of which checkout branch you are looking from), indicates the changes made in another branch which differs from the current branch. 
	- **You will only get a new git log if you COMMIT to a git branch.**
	- options: (options use are not mutually exclusive)
		- --all:
		- --graph: To get a visual of the commits in each branch, across its timeline
		- --raw: 
			- Data obtained:
				- commit identifier
				- commit branch 
				- commit author
				- commit date
				- commit information (for a single commit) - inode number of file, Name of file, file's state
	- Committed file state:
		- A - Added
		- M - Modified
		- R - Renamed
		- D - Deleted
	- Result: It will show the commit logs. Press 'q' to exit log view
## Git reset
```
git reset --soft {commit-id}
```
- Move the current HEAD pointer to the specified earlier commit-id, where the later commits  will be kept in the staging area, ready to be recommitted.

Show and delete git branch
- `git branch -a`: Show local and remote branches 
- `git branch -r`: Show only remote branches
- `git branch`: Show only local branches 
- `git branch -d {name_of_branch}`: Deletes branch/ remove branch in local repo
- `git push origin --delete feature/login`: Deletes branch in remote repo.

Switch between git branches
- `git checkout`
	- [Types of Git branches](https://gist.github.com/digitaljhelms/4287848)
	- Use: 1) Switch branches, 2) Restore working tree files
		- There are also new commands that do the two operations above separately - git switch, git restore (which is newly created to reduce confusion, https://stackoverflow.com/questions/57265785/whats-the-difference-between-git-switch-and-git-checkout-branch )
		- ![[git_checkout_vs_switch_and_restore.png | 500]]
- git checkout {another_existing_branch}
	- Changes your current branch to another existing branch
- git checkout -b {new_branch} 
	- Creates a new branch. Creates a copy from the main branch.
	- "new_branch" Naming convention: 
		- "feature/{new_branch_name}"
		- "feature-issue_no-{...}-{new_branch_name}"
- `git diff {optional: compare_branch_name}`
	-  Compares the code in the current branch, with you last commit in the same current branch. (Where the '+' symbols denotes that it is a new change)
	- {compare_branch_name}
		- Compares the code in the current branch, and the branch name that was specified for comparison, and shows: 1) Files that were modified, 2) The contents within said files, and their respective changes in the current branch vs that is being changes in the new branch. 
- `git merge {the_branch_we_want_to_merge_to_our_current_branch} -m {"text_commit_message"}`
	- Takes code from the specified branch name, and merge it to the current branch
	- It is considered a "commit", hence 1) we will need a commit message (`-m "{text_message}"`) 2) It will show up in git log as a commit node.
> 	"git merge master" is a good way to keep the branch you are editing, updated to the newest master branch, therefore when it comes time to merge to master branch, only a small amount of non-conflicting code can be commited. (You do not want to be left behind of all the newest changes, before you merge the code. It will make it way harder to resolve conflicts in the future.)

Deleting merged branches
1. Check for merged branches
```
git branch --merged
```
2. Delete merged branches
```
git branch -d {branch_name}
```
- Git will prevent you from deleting a branch with the command below if the two branches are not merged.
- Force delete a branch, even if it contains unmerged changes.
```
git branch -D {branch_name}
```

Pushing a branch to remote repo
- By default, when you stage (`git add`), commit (`git commit`), and push (`git push`) code, Git does not automatically push the branch to the remote repository. Instead, it only affects your local repository:
- To push a created branch into the remote repository: When you run `git push`, you specify the remote repository and branch you want to push.
```
git checkout <branch-name>
git push origin my-feature-branch
```
- 1. Ensure that you are in the local branch you want to push
- 2. Push the branch to GitHub

## Git remote
- Link a remote repo to your local repo.
```
$ git remote add {remote_identifier} {git_remote_link}
```

- View/ check all remote repo you have linked to the local repo
``` 
$ git remote -v
```

- Delete/ remove remote repo 
```
$ git remote remove <remote_name>
```

# Git fetch
```
$ 
$ git fetch upstream
```
`git fetch` updates your remote-tracking branches under `refs/remotes/<remote>/`. This operation is safe to run at any time since it never changes any of your local branches under `refs/heads`.

# Git pull
> By default: [`git pull`](http://git-scm.com/docs/git-pull) does a [`git fetch`](http://git-scm.com/docs/git-fetch) followed by a [`git merge`](http://git-scm.com/docs/git-merge).
> `git pull` runs `git fetch` with the given parameters and then depending on configuration options or command line flags, will call either `git rebase` or `git merge` to reconcile diverging branches.

#### Fetch + merge (*default `git pull`*)
Pull changes from upstream remote (e.g., you forked a repo, and upstream is the original repo that was forked), then attempts merge them and resolve conflicts. 
```
$ git remote add upstream {upstream_git_link}
$ git fetch upstream
$ git merge upstream/{remote_branch_name}
```
If this is done in a terminal, a GNU nano text editor will be brought up as the default Git commit message editor or for resolving merge conflicts interactively.
- To save your changes and exit `nano`, press `Ctrl` + `O`, then press `Enter`, and finally press `Ctrl` + `X`.
- To navigate and edit the text in `nano`, use the arrow keys and standard text editing commands.
	- We can use vim instead:
	- `git config --global core.editor vim`

#### Fetch + rebase
```
$ git merge --rebase upstream/{remote_branch_name}
```

# Git diff
Checking difference between 2 branches
```
git diff upstream/{branch_name} {path/to/file}
```

# Git stash
Use: Use to save work that is in progress, that you do not want to commit. Set aside your progress.
Common scenarios where git stash is nice to have/ helpful:
1. **Performing a Git Pull**:
    - If you have local changes that conflict with the changes you're trying to pull, Git won't allow the pull operation to proceed.
    - You can handle this by either committing your changes first and then pulling, OR you can use `git add --all` and `git stash` everything in the staging area to temporarily set aside your changes, perform the pull, and then reapply the changes with `git stash pop`.
```
git add --all
git stash
git pull origin branch_name
git stash pop
```
2. **Switching Branches with Git Checkout**:
    - When you want to switch branches using `git checkout {another_branch}`, but have uncommitted changes that could be overwritten or that conflict with the target branch, Git may block the checkout.
    - To resolve this, you can either commit your changes on the current branch first before switching, OR use `git stash` to stash your changes, switch branches with `git checkout`, and then return to your original branch later to reapply the stashed changes."
- 
# Git fetch
> A command used to **download data from a remote repository without merging it into your local working directory.** It essentially brings you up to date with the latest changes on the remote server.

- When a branch in your remote repository does not exist in your local repository. (e.g., You have 3 branches in remote repo, but your local repo only has 1 --- `main`)
```
# Fetch specific_branch_name branch from remote origin repo 
$ git fetch origin {specific_branch_name} 
```

# Git push
> If you want to submit a "pull request" using a forked repo, we typically do not need to "push" to the remote upstream.

- `git push {optional: flag} origin {optional: existing_branch}`

Pushing a branch to remote git 
```
$ git push origin feature-id                        // makes the new feature remotely available
```
Pushing to master
```
$ git push origin master
```

- Caveat: It can only be pushed if a remote repository is created/ exists and recognized. (If remote repository is created, but not connected: refer to "`git remote add origin {link}`")
- "origin" == "remote repository"
- flag:
	- -u/ --set-upstream: "Upstream", Sets the specified branch as the default branch to push to if origin and branch is not specified

