Using git and GitHub
====================

Initial Steps
-------------
1. [Join](https://github.com/join) GitHub.
2. Choose a folder on your machine for code repositories to live (optional).

Accessing a code project
------------------------
1. [Fork](https://help.github.com/articles/fork-a-repo/) the repository. 
This creates an identical copy associated with your account. 
This is a new 'remote' repository. It's a repository because it keeps track of 
changes to files, and it's 'remote' in that it doesn't live locally on your machine.
2. [Clone] (https://help.github.com/articles/cloning-a-repository/) the fork you've 
just created (your remote version of the project). Forking a repository will redirect 
you to the main page for your remote, or you can navigate there from your account's 
"Your Repositories" page. To create the clone, navigate to the folder on your machine 
in which you'd like to place the new repository, then execute `git clone <URL>`, where 
`<URL>` is copied from the `Clone or download` link on the remote repository page. 
If you [set up SSH access] (https://help.github.com/articles/connecting-to-github-with-ssh/), 
you can use the SSH URL. Otherwise, you can use the HTTPS URL. Executing this clone 
command will create a new directory within the folder in which you executed it.
3. `cd <repo-name>` to navigate into the newly-created repository folder.
4. You can run `git status` and `git remote -v` to confirm that you're on the `master` branch, 
and that your `origin` remote points to the remote repository from which you've cloned.
5. In the web UI, navigate back to the team/group/lab version of the repository (the 
one that was 'forked' to create your personal remote copy), and copy the URL from there 
as you did to clone your own remote.
6. From within the main repository folder on your local machine, run 
`git remote add <name> <URL>`, where `<name>` is arbitrary and is whatever you want to call 
your team/group/lab remote. This will likely often be used when issuing commands in the 
future, so something meaningful but short is best. Most git and GitHub documentation 
and web resources will use the term `upstream` to denote this sort of remote, so that 
is often a good choice.

Concepts
--------------
- Repository: a collection of code, either on your local machine or on a remote server.
- Branch: a particular version of a repository

Making changes
--------------
1. Decide what branch you'd ultimately like to merge your changes into (e.g., `master` or `dev`).
2. In your local repository, `git checkout <branchname>` to switch to that branch.
3. Run `git pull <remote> <branchname>` to update your local repository with the most recent 
version of the team/group/lab branch, where `<remote>` is whatever you've named the team version 
of the repository, and `<branchname>` is the name of the general-purpose branch you plan to 
ultimately integrate changes to. (You can check available remotes locally with `git remote -v`.)
4. Run `git checkout -b <newbranch>` to create a new feature/fix branch, and switch onto it. At 
this moment, this new branch and the one from which you branched are identical. You can check 
your current branch with `git branch`, and if you decide you'd like to rename a branch, you can 
run `git branch -m <newname>`.
5. As you make changes, it's best to `commit` them occasionally in your local repository. This 
builds up a log of changes. This doesn't need to be done constantly, but multiple times per day 
is not uncommon. Often, it makes sense to do this once you've successfully tested a small batch 
of changes locally.
6. To commit, you first "stage" the changes you've made with `git add <path1> <path2> ...`, where 
you can stange multiple files in one pass. You then `git commit -m "<message>"` to record the changes 
and provide some context. A nice shortcut for staging/adding and committing changes at the same 
time is `git commit -a -m "<commit message>"`.
7. Whenever you want to put the changes into your personal remote copy of the repository, you can 
`git push origin <branchname>` to do so.

Requesting to integrate changes
-------------------------------
When using a this sort of `git` workflow, this is as easy as opening a 
[pull request](https://help.github.com/articles/creating-a-pull-request-from-a-fork/) from 
your personal remote's feature/fix branch to a target branch in the team/group/lab remote.

Best practices
--------------
- Generally, a project/repository will have some generic branches (`master` and `dev`) 
are common.
- These names are not magic, but they are commonly used to denote the core, stable version 
of a project (`master`) and the latest development version with new features (`dev`).
- Routinely (at least daily, and more often if the rate of change integration is quick), 
`pull` new changes from the team/group/lab version of the branch you're planning to merge 
your feature or fix branch into. This will minimize the probability of conflicting changes 
and keep such conflicts relatively small and manageable if they do arise.
- It's best to keep clean working versions of each such general-purpose branch, and work 
on separate feature- or fix-specific branches. This facilitates seamless switching between 
feature/fix branches, keeping groups of changes independent from one another. If changes are 
being made to the same lines of the same files, it's best to maintain a single branch with 
such changes to avoid "merge conflicts." Try to keep changes grouped into relatively small, 
logical units, so that you can integrate changes more frequently into a team project and so 
that reviews of changes do not become unwieldy.
- For projects that are released, `master` typically only changes when a new version of 
the software is released. A similar idea could be applied to a code project/repository 
that's used to, say, generate output for multiple papers. The `master` branch could be 
reused, and a new version [tagged](https://help.github.com/articles/creating-releases/) when 
a new paper is generated with the code.

Most useful commands
--------------------
1. `git pull <remote> <branch>` (getting changes from a web remote to your local repository)
2. `git push <remote> <branch>` (moving local changes to your personal remote web repository)
3. `git fetch --<remote-name>` or `git fetch --all` (getting branches and tags from web remote(s))
4. `git checkout <branch>` (switch branches)
5. `git branch <branch>` (create new branch)
6. `git add [files...]` (stage changes for commit)
7. `git commit -m "<message>"` (commit staged changes)


