

**Creating Commits**

In Git, version = commit

Version history = commit history

git init

Git will start tracking all changes in the current folder

git status

Show all changes since the previous commit

git add <file|folder>

git add file

Pick changes to go into next commit

Pick individual ﬁle

git add folder/

git add .

Pick all ﬁles inside a folder (and subfolders)

Pick all ﬁles (in folder command line is running in)

git commit -m "message"

Creates a commit with a message attached

git commit -m "message" --amend

Update previous commit instead of creating new one

git log

View the commit history

git log --all

git log --all --graph

Show all commits (not just current branch)

Show branching visually in the command line

**Conﬁgure Name & Email for Commits**

git config --global user.name "Your Name"

git config --global user.email "email@example.com"

**Working Area** = contains changes start in the working area



<a name="br2"></a> 

**Staging Area** = contains changes that will go into the next commit

git add .

working => staging

git commit -m "message"

staging => commit history

git reset <file|folder>

git reset file

staging => working

git reset folder/

git reset .

git checkout -- <file|folder>

git checkout -- file

git checkout -- folder/

git checkout -- .

working => remove the changes

**Viewing Previous Commits**

git checkout <commit\_hash|branch\_name>

View a previous commit

**master** = branch name

1\. You can git checkout branch

2\. Always points to latest commit

on the branch.

**HEAD**= indicates which commit

you are currently viewing

**Restoring to a Previous Commit**

git checkout <hash|branch> <file|folder> Restore the contents of ﬁles back to a

previous commit

git checkout <hash|branch> file

git checkout <hash|branch> folder/

git checkout <hash|branch> .

Restore a ﬁle

Restore all ﬁles in folder (& subfolders)

Restore all ﬁles in project

**Other Features of Git**

git config --global alias.shortcut <command> Creates an alias (a shortcut)

git config --global alias.s "status" git s = git status



<a name="br3"></a> 

.gitignore

rm -rf .git

Tell git which ﬁles/folders it SHOULD NOT track

Remove git from project

**GitHub**

Repository = a folder containing code where any changes to the code are tracked by git.

(To create a repository, we create a new folder on our computer, and then run git init)

GitHub = a service that lets us save our git repositories online. It also helps us:

\- backup our code in case we delete it on our computer

\- see the history of our code changes more easily

\- alternatives include Bitbucket and GitLab

Local repository = a git repository saved on our computer

Remote repository = a git repository saved online (for example on GitHub)

**Uploading Code to GitHub**

git remote add <remote\_name> <url> Link a local repository to a remote repository and

give a name for this link

git remote add origin https://github.com/SuperSimpleDev/repository1

^

The above command links a local repository to a GitHub repository (located at the url

https://github.com/SuperSimpleDev/repository1) and gives it a name "origin"

git remote

List all remote repositories that are linked

git remote -v

List all remote repositories (but with more detail)

git remote remove <remote\_name>

git remote remove origin

Removes a link to a remote repository

Removes the link to the remote repository named

"origin"

git config --global credential.username <username>

Conﬁgure your GitHub username so you can get

access to your Github repository

git push <remote\_name> <branch>

Upload a branch of your git version history to your

remote repository

git branch

Shows a list of available branches

git log --all --graph

Shows the branches visually in the history



<a name="br4"></a> 

git push origin main

Upload the branch "main" to the remote repository

named "origin"

git push <remote\_name> <branch> --set-upstream

Sets up a shortcut for this

branch and remote repository

Next time you are on the main

branch and you run git push, it

will automatically push the

mainbranch to origin

git push origin main --set-upstream

git push <remote\_name> <branch> -f Force-push the branch to the remote repository (it

will overwrite what's on the remote repository)

**Downloading Code from GitHub**

git clone <url>

Download a remote repository from a url

git clone https://github.com/SuperSimpleDev/repository1

git clone <url> <folder\_name>

git fetch

Download the repository and give it a different

folder name

Updates all remote tracking branches. Remote

tracking branches (like origin/main) show what

the branch looks like in the remote repository

git pull <remote\_name> <branch>

git pull origin main

Update the local branch with any updates from

the remote repository (on GitHub)

Downloads any new commits from the main

branch on origin, and updates the local main

branch with those new commits

git pull origin main --set-upstream

^

Sets up a shortcut so that the next time you are on the mainbranch and run git pull, it will

automatically git pull origin main

**Branching**

Branching = create a copy of the version history that we can work on without affecting the

original version history. This lets us work on multiple things (features + ﬁxes) at the same time.

git branch <branch\_name>

git branch feature1

Creates a new branch

Create a new branch named feature1

git checkout <branch\_name>

git checkout feature1

Switch to a different branch and start working on

that branch

Switch to the feature1branch. New commits will

now be added to the feature1branch



<a name="br5"></a> 

**HEAD** = points to which branch we are currently working on

**HEAD ->** feature1= we are currently working on the feature1branch. Any new commits will

be added to the feature1branch

git branch -D <branch\_name>

git branch -D feature1

Deletes a branch

Deletes the feature1branch

**Merging**

git merge <branch\_name> -m "message" Merge the current branch (indicated by **HEAD ->**)

with another branch (<branch\_name>). Saves

the result of the merge as a commit on the

current branch

git checkout main

1\. First switch to the mainbranch

git merge feature1 -m "message"

2\. Then merge the mainbranch with the

feature1branch. The result of the merge will be

added to mainas a commit (a "merge commit")

**Merge Conﬂicts**

<<<<<<< HEAD

code1

\=======

If there is a merge conﬂict (git doesn't know

what the ﬁnal code should be), it will add this in

your code.

code2

\>>>>>>> branch

(This is just for your convenience, the <<<<<<<

and >>>>>>>don't have special meaning)



<a name="br6"></a> 

<<<<<<< HEAD

...

\=======

<-- Code in the current branch (indicated by **HEAD ->**)

<-- Code in the branch that is being merged into **HEAD**

...

\>>>>>>> branch

**To resolve a merge conﬂict:**

1\. Delete all the extra code and just leave the ﬁnal code that you want.

~~<<<<<<< HEAD~~

~~code1~~

~~=======~~

=> code2

code2

~~>>>>>>> branch~~

2\. If there are conﬂicts in multiple places in your code, repeat step 1 for all those places.

3\. Create a commit.

git add .

git commit -m "message"

**Feature Branch Workﬂow**

A popular process that companies use when adding new features to their software.

1\. Create a branch for the new feature (called a "feature branch").

git branch new-feature

git checkout new-feature

Make some changes to the code...

git add .

git commit -m "new feature message"

2\. Upload the feature branch to GitHub.

git push origin new-feature

3\. Create a pull request on GitHub (a pull request lets teammates do code reviews and add

comments).



<a name="br7"></a> 

4\. Merge the feature branch into the main branch (by opening the pull request in the browser

and clicking "Merge pull request")

5\. After merging, update the local repository (so that it stays in sync with the remote repository

on GitHub).

git checkout main

git pull origin main

**Merge Conﬂicts in the Feature Branch Workﬂow**

A merge conﬂict can happen if 2 or more pull requests change the same ﬁle and the same line.

We can either:

1\. Resolve the merge conﬂict on GitHub.

2\. Resolve the merge conﬂict on our computer.

\1) Get the latest updates from main

git checkout main

git pull origin main

\2) Get the latest updates from the feature branch\.

git checkout feature4

git pull origin feature4

\3) Merge maininto the feature branch (feature4)\. Notice the direction of the merge: we want

the merge commit to stay on the feature branch so our teammates can review it.



<a name="br8"></a> 

git checkout feature4

git merge master

\4) Push the resolved feature branch to GitHub\.

git push origin feature4

Now the pull request should be ready to merge again.

