
# Github concepts

How do you recognize a directory in your workspace is a git repository?
- .git (a directory) is created within the directory.

Git data sites:
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

"pull request" (PR)
- A request sent to allow you code from your branch ("compare branch") to be pulled into another branch ("the base").
- If you are not the owner of a repo,often times you do not have access to the master branch. This means you cannot push the code directly to master, where they can only push the code to a different branch, and then raise a pull request to merge the changes to "master" branch.
- Once a pull request is accepted and merged to another branch, the life cycle of your own branch can end, delete the branch.
- Git hub: (remote repository - where the primary changes are done to if you use the github interface on web to make changes.), where if the developer wishes to see the changes, they have to use "git pull " command.
	- There is a button called "Pull requests" at the navigation bar. 
	- You can check comments, you commits, changes to the branch you have submitted for pull request.
- Terminal git: (local repository - where the primary changes are done), where additional commands is required to push to remote repo.

## Git branching
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
"Merging"
- The process of combining code from two branches.
![[git_merging.png]]

"Forking"
- Copying an ENTIRE repo to your own repo
- You would do that if you want to refactor someone's (a random guys) entire repo, because you want to make changes to multiple branches, even if you are not assigned that branch, while you are not the owner. OR you just feel like experimenting with other people's code for fun. (It is similar to cloning people repo, create you own repo, copy their entire repo to your newly created repo, and commiting to your local repo, and pushing to you remote repo)
- Similar to merging to base (the master branch) in branch merging, we have repository merging.
- We can create a "pull request" to merge the "forked repo" to the "base repo", or go more intricately, and merge the "fork repo's specific branch" to the "base repo's same branch"


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

- `git add {target}`
	- Asks git to "add" all "untracked" files IN the local workspace by "staging" it TO "the Index".
	- Target:
		- --all
		- .
		- {filename}
		
- UNDO STAGING: git reset {optional: name_of_the_file}
	- Unstage all staged files from the Index 
	- {optional: name_of_the_file}
		- unstage the specified file from the Index
	- When you type git staus again, you will see that the files are "unstaged and modified"

- `git commit -{flag} {commit message} {optional: {description of the commit message}}`
	- -m {commit message}: Commits the "staged code" at index to the local repository. (Note that code has to be staged and recognized by the Index before it can be committed.)
	- -am {commit message}: Commits the "staged code" at index to the local repository. (Note that code has to be staged and recognized by the Index before it can be committed.(This can only be used on "tracked" file/ files that was staged before,and are currently just "modifiying")

## Git branching
A copy of the main/ master branch version at the time when the branch is created.
- Resources:
	- [Youtube video: Git branching and merging - Detailed tutorial](https://www.youtube.com/watch?v=Q1kHG842HoI)

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

- UNDO COMMITS: git reset {HEAD{optional:~{n commits before}}} OR git reset {commit_hash}
	- Uncommits you last commit 
	- HEAD: a pointer to the last commit 
	- HEAD{optional:~{n commits before}}: uncommits the last N commits further starting from the last commit.
	- {commit_hash}: An identifier given to a specific commit. (This identifier can be found after using the "git log" command).


- `git branch -{optional: flag} {optional: name_of_branch}`
	- Shows the branches (if we only enter: "git branch" in the terminal), where an (\*) astrisks is used to denote the branch you are currently working on, press 'q' to exit branch view mode.
	- flags:
		- -d {name_of_branch}: Deletes branch in local repo
- `git push origin --delete feature/login`
	- Deletes branch in remote repo

- `git checkout`
		- Use: 1) Switch branches, 2) Restore working tree files
			- There are also new commands that do the two operations above separately - git switch, git restore (which is newly created to reduce confusion, https://stackoverflow.com/questions/57265785/whats-the-difference-between-git-switch-and-git-checkout-branch )
			- ![[git_checkout_vs_switch_and_restore.png | 500]]
	- git checkout {another_existing_branch}
		- Changes your current branch to another existing branch
	- git checkout -b {new_branch} 
		- Creates and changes you current branch to the new branch.
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

- `git push {optional: flag} {origin} {optional: existing_branch}`
	- Caveat: It can only be pushed if a remote repository is created/ exists and recognized. (If remote repository is created, but not connected: refer to "`git remote add origin {link}`")
	- flag:
		- -u/ --set-upstream: "Upstream", Sets the specified branch as the default branch to push to if origin and branch is not specified

