# git

## Courses

| Title                                                                                                                                                         | Status |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ |
| [How Git Works - Zines](https://wizardzines.com/zines/git/) [⚓](./01%20How%20Git%20Works/)                                                                   |        |
| [Getting Started with Git](https://app.pluralsight.com/library/courses/git-getting-started/table-of-contents) [⚓](./02%20Getting%20Started%20with%20Git/)    |        |
| [Git: The Big Picture](https://app.pluralsight.com/library/courses/git-big-picture/table-of-contents) [⚓](./03%20Git:%20The%20Big%20Picture/)                |        |
| [How Git Works](https://app.pluralsight.com/library/courses/how-git-works/table-of-contents) [⚓](./04%20How%20Git%20Works/)                                  |        |
| [Mastering Git](https://app.pluralsight.com/library/courses/master-git/table-of-contents) [⚓](./05%20Mastering%20Git/)                                       |        |
| [Working with Git Branches](https://app.pluralsight.com/library/courses/git-branches-working/table-of-contents) [⚓](./06%20Working%20with%20Git%20Branches/) |        |

---

```bash
which git
git --version
```

```bash
C:\Users\venka>git hash-object "Apple Pie"
fatal: Cannot open 'Apple Pie': No such file or directory

C:\Users\venka>echo "Apple Pie" | git hash-object --stdin
23991897e13e47ed0adb91a0082c31c82fe0cbe5

C:\Users\venka>echo "Apple Pie\n" | git hash-object --stdin
5e009b67767799d558fe67a89db17f6a02a6ab36

# to write content into the git repository
C:\Users\venka>echo "Apple Pie\n" | git hash-object --stdin -w
5e009b67767799d558fe67a89db17f6a02a6ab36
```

## What is Git?

```text
    Version Control System
        Software Designed to record changes made to files over time
        Ability to revert back to a previous file version or project version
        Compare changes made to files from one version to another
        Version control any plain text file, not just source code.
    Git is a Distributed Revision Control System.
    Git is a Revision Control System.
    Git is a Stupid Content Tracker
    Git is a Persistent Map
        Values(Any sequence of bytes-"Apple Pie")  and
        Keys (SHA1 hash-23991897e13e47ed0adb91a0082c31c82fe0cbe5)
    Every  object in Git has its own  SHA1.
    SHA1s are unique in the universe.
    Git(mostly) doesn't care about your working directory
```

## What is Git useful to?

```text
    Git tracks changes to source code.
    Version control isn't a backup.
    Version control is useful to track a project's history.
    Version control is useful to Managing Multiple Versions of a Project.
    Version control is useful to share code amongst developers.
    Version control is useful to coordinate teamwork.
```

## Three Rules

```text
    1. The current branch tracks new commits
    2. When you move to another commit, Git updates your working directory
    3. Unreachable objects are garbage collected
```

## The Two Questions

```text
    1. How does this command move information across the Four Areas?
    2. How does this command change the Repository?
```

## The Three States of a Git Project

```text
Working Directory:- Changes to files since the last checkout have not yet been added to the staging area for commit.
```

```text
Staging Area (Index):- Files in this state have been modified and added to be staged in the next commit snapshot.
```

```text
.git directory(Repository):- Files in this state are committed and recorded to the project as version snapshots
```

## The Four Areas

1. Stash
2. Working Area
3. Index
4. Repository

## Stages of a File

1. Committed

   ```text
       Unmodified changes from the last commit snapshot
       Belong to branch
           Changes not visible when switch branch
   ```

2. Modified

   ```text
       Changes made to files since last commit snapshot
       Modified status to file applies only, which files are tracking in the git already.
   ```

3. Staged(Index)

   ```text
       Changes marked to be added into the next commit snapshot
       Marked changes have been added to the commit snapshot
       Added and ready for commit
           Stay in staged state
   ```

4. Untracked

   ```text
       Not added or committed
           Stay in directory.
   ```

5. Tracked

   ```text
       tracked files, those in previously committed to the repository.
       we can stop tracking the files which tracked earlier.
   ```

## the following three terms are same

```text
    1. staged (like --staged)
    2. cached (like --cached)
    3. index (like --keep-index)
```

## Git Objects

```text
    Blobs
    Trees
    commits
    Annotated Tags
```

## Branch

```text
    A branch is just a reference to a commit
    HEAD is just a reference to a branch
    Git updates filesystem when change branches
        Open editors reflect changes
    Branches help you organize your work
    Changes are isolated in each  branch
    File system automatically updates when switch branches
    Cleaner and less error-prone than trying to do it yourself without branches.
```

## How To's

1. What changes have i staged that are ready to be committed?

   ```bash
   git diff --staged
   ```

2. What changes have i made but not yet staged?

   ```bash
   git diff
   ```

3. We can stage partial changes in single file with the following

   ```bash
   git add -p
   ```

4. gotcha:

   ```bash
   git commit -a # doesn't automatically add new files
   ```

5. We can print the current branch name with the following command

   ```bash
   cat .git/HEAD
   ```

6. This command commits the current staged changes to the repository with the provided commit message, skipping any hooks.

   ```bash
       git commit --no-verify -m "Commit message"
   ```

## Ignore File (`.gitignore`)

1. Files are Tracked, Untracked, Ignored.
2. Generated files are usually Ignored
3. Ignored files not added to branches
4. `.git/info/exclude` - Ignore patters for your System only

```text
*  (anything)
?  (one character)
!  (negator)
/  (directory separator)
[a-zA-Z] (range)
```

### Example of `.gitignore`

```bash
# this is a comment (# for comments)
**/bin   # ** matches any directory in Repository
*.zip    # * matches any file in Repository
/bin     # relative to .gitignore directory Put a .gitignore at your project root
```

## Insights

```shell
git  cat-file -p 5f7b681a3621ceee721e541d725de52dc3117a63
# 5f7b681a3621ceee721e541d725de52dc3117a63 is the sha1 hash of the contents of the file.
# It's called a blob id. Commit and tree IDs are hashes too.
# Using  a hash to  identify each file is how git avoids duplication: if the file's contents don't change, the has won't change, so git doesn't need to store a new version.
```

1. `git rm` is not the opposite of `git add`
2. git automatically finds out when you're renaming or moving files.
3. `revert` doesn't mean "undo".

## R&D

1. Client-Server Version Control?
   Distributed Version Control?
   - Like a local branch, a remote branch is jut a reference to a commit.
   - Flow: You fetch and merge, then you push.
   - Flow You pull, then you push.
2. Detached HEAD?
3. git diff --histogram
   explore diff algorithms
4. How Rebase works?

   - Rebases refactor history
   - Never rebase shared commits
   - Rewriting Large Chunks of History?
     - We have a huge file in the Repository
     - We committed our passwords!
   - Overview
     - Squash several commits into one
     - Replay commits from another branch
     - Clean up local history
       - before sharing a branch
       - Focus on end result
     - Should increase accuracy and clarity
     - Rough draft vs. final copy
     - Rebase is an advanced feature
       - Not mandatory
       - It can cause problems
       - Times to NOT use it

5. How Merge works?
   Merges preserve history
6. Rebase vs. Merge?
   When in doubt, just merge
7. Tag
   A tag is like a branch that doesn't move
8. Cherry-pick
   Overview

   - Get a commit without merging branch
   - Apply a bugfix to Multiple branches
   - Copy specific commits to another branch
   - Bugfix for Multiple versions of product
   - Capture commits from inactive branch
   - Move specific commits to your branch
     - Features needed for your ticket
     - Branches not ready to merge yet
   - Create duplicate commit in each branch
     - Can cause confusion
   - Cherry-pick is an advanced feature
     - Should not replace merge

## Q&A

1. What are the three stages of a file?

   - Committed
   - modified
   - staged

2. Which of these is a valid reason to use Git?

   Git is fast

3. What's the relation between Git and GitHub?

   GitHub is an online service based on Git

4. When does Git create a new snapshot of the project?

   When you ask it explicitly to do that

5. What happens when you give the git init command?

   you create a new empty Git repository

6. Which Git command initializes a new Git repository in your terminal or command?

   ```shell
      git init
   ```

7. Which Git command sends your local project to the remote origin?

   ```shell
   git push
   ```

8. Which Git command is used to move a file from the staging area to the .git directory?

   ```shell
   git commit
   ```

9. Which command prompt command returns your current folder path location?

   ```shell
   pwd
   ```

10. Which Git command do you use to set your global user.name configuration?

    ```shell
    git config --global user.name "your-user-name"
    ```

11. Which Git command moves changes from committed to the staging area?

    ```shell
    git rest --soft
    ```

12. Which Git reset command moves changes from committed to the trash?

    ```shell
    git reset --hard
    ```

13. A small team of three developers decide to integrate their code by always committing to the main branch master. Which of these sentences do you think describes the situation?

    This way of working might be the right way for them, depending on the specific details of the project.

14. You have an application that must be deployed to three customers. Each customer needs its own version of the application, with many small features that are specific for that customer. How would you set up this project in a version control system?

    You create three branches, one for each customer.

15. Three developers work by creating a new branch for each new feature. (Those are sometimes called "feature branches".) When a feature is done, the team merges the feature branch into master and deletes the branch. Which of the following facts is true?

    The team might have merge conflicts, but the conflicts will be easier to solve if feature branches last for a shorter time.

16. A company is migrating from Subversion to Git, and they plan to use Git in a way that's similar to the way they used Subversion: a shared repo on a central server, that all developers' machines connect to. Is that possible in Git?

    Yes-each developer will have a copy of the repo, but they can all keep a central shared repo as their "remote".

17. Which of these is not a typical task for the build machine in a software development project?

    Committing new changes to the main master branch.

18. What happens if the repository server in a client-server version control system goes down for maintenance?

    The developers in the team can still write code, but they can't share their changes.

19. Frank wants to fork Bob's project on GitHub. Which of these facts is true?

    If Bob's project is public, then Frank can fork it freely.

20. What do you do when you "commit a file" in Git?

    You create a snapshot that contains the current state of the file

21. Which statement is true regarding branches?

    A branch is a pointer to specific commit in your project.

22. Which Git command shows you the changes you've staged that will go into your next commit?

    ```shell
    git diff --staged
    ```

23. Which Git command can you use to see the full git help manual?

    ```shell
    man git
    ```

24. Which Git commands create a new branch and checks out to it at the same time?

    ```shell
    git checkout -b new_branch_name
    ```

25. Which Git command shows you the state of your working directory and staging area?

    ```shell
    git status
    ```

26. Which Git command skips the staging area when adding a change from our working directory?

    ```shell
    git commit -a -m "your-commit-message"
    ```

27. What happens to unreachable objects in the database?

    They can eventually get garbage-collected.

28. What's a "pull"?

    A "fetch" followed by a "merge"

29. What are the four types of objects in the Git database?

    Blobs, Trees, Commits and Annotated Tags

30. Which of these is a reserved remote name that you can't use yourself?

    Mostly none of the branch names are reserved. using branch names are conviction

31. Can an object in Git be safely modified?

    No: if you changed even one bit, then you'd get a different object with its own SHA1.

32. What's one difference between merges and rebases?

    Rebases change history, merges don't

33. How does "git rebase" move an existing commit?

    It copies over the commit to a new commit with a different parent and SHA1.

34. What happens if you merge a branch with itself? or What happens if you rebase a branch over itself?

    Nothing

35. What is "origin"?

    Just a conventional name for your main remote.

36. Which of these is NOT a Git command?

    git fork

37. Which objects are created when you merge?

    Zero or one commit, and possibility new trees and blobs

38. What happens when you commit?

    The current branch changes, HEAD doesn't

39. Where does Git store the names of files and directories?

    in the object database, inside the trees that point to the objects.

40. What is the problem with git force --push?

    There is no such command.

41. Which objects in Git have a SHA1 hash?

    Each object in the database.

42. How many parents can a commit have?

    Zero or more

43. Where can HEAD point?

    To a branch or a commit

44. Why does Git use Secure Hash Algorithm 1 (SHA-1) encryption internally?

    To identify and verify the integrity of all file objects and commits

45. What command can result in a fast-forward?

    pull

46. Which command narrows the search to locate which commit introduced a bug?

    git bisect

47. After writing the command git checkout {branch-name} numerous times, you want to abbreviate the name of the command. You run the command git config --global alias.co checkout and expect an alias to be set. What happens if you then type git co {branch-name}?

    The checkout command happens as expected; the alias was set successfully.

48. You pull the latest changes from your project's remote repository and you notice a few merge conflicts. Which command will run Git's conflict resolution tools?

    git mergetool

49. The sole difference between branches b1 and b2 is that b2 contains a file that b1 does not. When you merge branch b1 into b2, it results in a conflict. What is the most likely explanation?

    The file was modified on b2 and deleted from b1.

50. What is the difference between comparing two branches with git diff or git difftool?

    git diff uses the command-line diff command, while git difftool uses the external diff tool that you configured.

51. What is the difference between git branch -d <your_branch> and git branch -D <your_branch>?

    The -d flag deletes the local branch only if it has been merged with the remote branch, while the -D flag forces the deletion of the local branch without checking its remote state.

## Commands

```bash
git add [filename] # Stages the specified file or directory.
git add '*.txt'  # Stages only text files. It will not stage deleted text files.
git add .        # stages all new and modified files in the current directory and its subdirectories, but it does not stage deletions.
git add -A       # Stages all changes, including new files, modified files, and deleted files.
git add -u       # Stages changes to tracked files only (modifications and deletions, but not new files).
git add *  # Adds all non-hidden files and directories in the current directory

```

```bash
git annex add mybigfile # Add 'mybigfile' to the annex, tracking it without storing its content in the Git repository
git annex copy --from myremote mybigfile # Copy 'mybigfile' from the remote 'myremote' to the local annex
git annex drop mybigfile # Remove the content of 'mybigfile' from the local repository, keeping it only in the annex
git annex get mybigfile # Retrieve the content of 'mybigfile' from the annex back to the local repository
```

```bash
git bisect start # Enter bisect mode to start the binary search for the commit that introduced a bug
git bisect good  # Mark the current commit as good (i.e., the bug is not present in this commit)
git bisect bad   # Mark the current commit as bad (i.e., the bug is present in this commit)
git bisect log   # Show the log of good and bad commits identified during the bisect process
git bisect reset # Exit bisect mode and return to the original commit, cleaning up any bisect state
```

```bash
git blame recipes/apple_pie.txt # Show line-by-line history of 'recipes/apple_pie.txt' with corresponding commits and authors
```

```bash
git branch                        # List all local branches
git branch --delete branchname    # Delete the merged branch "branchname" (only possible if not the current HEAD)
git branch --merged               # Show all branches that are completely merged with the current branch
git branch --move branchname new_branchname # Rename the branch "branchname" to "new_branchname"
git branch -a                     # List all branches, including remote branches
git branch -d [branch]            # Delete the local branch "[branch]"
git branch -D branch_to_delete    # Hard delete the branch "branch_to_delete" even if it is not merged
git branch -d branchname          # Delete the local branch "branchname"
git branch -D branchname          # Hard delete a local branch, will not complain if the branch is not merged (like `rm -rf` in bash)
git branch -d branchname          # Soft delete a local branch, will complain if the branch is not merged
git branch -d branchname          # Soft delete the merged branch "branchname" (only possible if not the current HEAD)
git branch -m [MYBRANCH]          # Rename the current branch to "MYBRANCH"
git branch -m branchname new_branchname # Rename the branch "branchname" to "new_branchname"
git branch -r                     # List all remote branches
git branch [branchname]           # Create a new branch called "branchname"
git branch branchname             # Create a new branch called "branchname"

<<COMMENT

Delete a Branch
    Error message if unmerged commits (will lose that work)
    Can  force delete if sure
    Cannot delete current working branch
        Switch to a different branch first

COMMENT
```

```bash
# Open the GitHub issues page of the project
git browse -- issues

# Open the GitHub wiki pages of the project
git browse -- wiki

# Open the main GitHub page of the project
git browse

# Set the default web browser to Chrome for git commands
git config --global web.browser chrome

# Set the path to the Chrome browser executable
git config --global browser.chrome.path "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"

# Open the specified URL in the default web browser
git web--browse https://github.com/yourusername/yourrepository

# Open the GitHub repository page in the web browser using GitHub CLI
gh repo view --web
```

```bash
git cat-file -p mytag          # Show the content of the tag 'mytag', which includes the commit ID it points to
git cat-file -p mytag          # Show the content of the tag 'mytag' again (duplicate command)
git cat-file commit-Id -t      # Print the type of the object (e.g., commit, tree, blob) with the given commit ID
git cat-file commit-Id -p      # Print the content of the object with the given commit ID
```

```bash
git checkout -- <FILE> # Discard local modifications and reset to the last committed version of the specified file
git checkout -- cats.html index.html # Undo all changes made to 'cats.html' and 'index.html'
git checkout -- index.html # Undo modifications to 'index.html' (restore from the latest committed version)
git checkout --track origin/<MYBRANCH> # Create and track the remote branch 'MYBRANCH'
git checkout --track origin/abranch # Create and track the remote branch 'abranch'
git checkout -b [branch] # Create and switch to a new branch '[branch]'
git checkout -b <MYBRANCH> # Create and switch to a new branch 'MYBRANCH'
git checkout -b branchname # Create and switch to a new branch 'branchname'
git checkout -b mybranch origin/abranch # Create a new branch 'mybranch' and track 'origin/abranch'
git checkout -b new_branch
git checkout -b new-branch-name # Create and switch to a new branch 'new-branch-name'
git checkout . # Delete all local changes and restore the last commit
git checkout [branch] # Switch to the branch '[branch]'
git checkout @ -- index.html # Hard reset of 'index.html' to its state in the latest commit (HEAD)
git checkout <MYBRANCH> # Switch to the branch 'MYBRANCH'
git checkout 0c6de32 # Checkout a specific commit in detached HEAD state; use 'git checkout <BRANCH>' to reattach
git checkout 6eb715d -- index.html # Restore 'index.html' from a specific commit '6eb715d'
git checkout branchname » git rebase master # Rebase 'branchname' onto the tip of 'master'
git checkout branchname # Switch to the branch 'branchname'
git checkout branchname # Switch to the existing local branch 'branchname'
git checkout commit1 # Checkout a previous commit 'commit1' in detached HEAD state; use 'git checkout master' to reattach
git checkout filename # Checkout the specified file 'filename'
git checkout HEAD menu.txt # Restore 'menu.txt' to its state in the latest commit
git checkout HEAD~ # Checkout the previous commit in detached HEAD state
git checkout master; git merge branchname # Switch to 'master' branch and merge 'branchname'; conditions for fast-forward merge apply
git checkout new_branch
git checkout tagname # Checkout the code at the specified tag 'tagname'
git checkout v0.0.1 # Checkout the code at the specified tag 'v0.0.1'
```

```bash
git cherry-pick [commit id] # Apply the changes from the specified commit to the current branch
git cherry-pick 073791e7    # Apply the changes from the specific commit '073791e7' to the current branch
```

```bash
git clean -f # Forcefully remove untracked files from the working directory
git clean -f # Forcefully delete untracked files (not staging)
git clean -n # Show which untracked files would be removed (dry run)
```

```bash
git clone <URL>                   # Clone the entire repository history from the specified URL
git clone <URL> <DIR>             # Clone the entire repository history and rename the directory to <DIR>
git clone --depth=1 <URL>         # Clone the repository with a shallow copy, only the latest commit
git clone MYURL                   # Download the repository from 'MYURL' into a folder with the same name as the repository
git clone MYURL foldername        # Download the repository from 'MYURL' into a folder named 'foldername'
git clone <old repo>              # Clone the repository from 'old repo' (placeholder for actual URL)
git clone --depth 1 [repository_path] # Clone the repository with a shallow copy, only the latest revision
git clone [repository_path] [new repository_path] # Clone the repository and specify the name of the new directory
git clone [repository_path]       # Clone the repository from the specified path
```

```bash
git commit                     # Commit the staged changes to the repository
git commit --amend             # Amend the previous commit with new changes
git commit --amend --no-edit   # Amend the previous commit without changing the commit message
git commit --amend -m "New Message" # Amend the last commit with the message "New Message" and any staged changes
git commit -a                  # Commit all changes to tracked files
git commit -am 'message'       # Add and commit all changes from tracked files with the message 'message'


git commit -m "[comment]"      # Commit the staged changes with the message '[comment]'
git commit -m "Initial commit" # Commit the initial set of files with the message "Initial commit"
git commit -m "Title" -m "Description..." # Commit changes with a title and description

```

```bash
vim .git/config # Open the .git/config file in vim to view or edit all configurations of the git repository
git config --global --list # List all global-level (machine-level) configurations
git config --list          # List all configurations at the global or project level
git config --global color.ui true # Enable colored UI in git commands globally
git config --global core.editor vim # Set vim as the default editor for git globally
git config --global diff.tool meld # Set meld as the default diff tool for git globally

git config --global push.default current # Set the default behavior of 'git push' to push the current branch

git config --global user.email "localvenkateswara@hey.com" # Configure the user email at the system level
git config --global user.email # Get the configured user email at the system level
git config --global user.email foo@citrix.com # Configure the global user email as "foo@citrix.com"
git config --global user.name  # Get the configured user name at the system level
git config --global user.name "John Doe" # Configure the global user name as "John Doe"

git config user.email "localvenkateswara@hey.com" # Configure the user email at the project level
git config user.email # Get the configured user email at the project level
git config user.name  # Get the configured user name at the project level
git config user.name "local venkateswara tolla"   # Configure the user name at the project level

```

```bash
git count-objects # Print the number of loose objects and their disk consumption in the git repository
```

```bash
git diff --cached (git commit) # Show changes that are staged for commit
git diff --cached # Show changes between the staging area and the last commit
git diff --no-commit-id --name-only --no-merges origin/master... # Show file names of changes between the working directory and origin/master, excluding merge commits


git diff --staged --no-renames # Show staged changes, ignoring renames
git diff --staged # It compares between the staging area and the last commit
git diff --staged # Show changes that have been staged

git diff --stat # Show statistics of changes
git diff --word-diff # Show word diff instead of line diff


git diff # Display the differences of changed files
git diff # List unstaged changes to files
git diff # Show changes between the working directory and the staging area
git diff # Show the changes you've made to your files that haven't been staged yet
git diff # Show the difference between changes in your working directory and the staging area
git diff 0c6de32 HEAD # Compare the current commit to a previous commit (0c6de32)
git diff branch-name # Show changes between the working directory and the specified branch
git diff branch1 branch2 # Compare two branches
git diff commit1 commit2 # Show differences between two commits
git diff feature master # Show differences between the tips of branches 'feature' and 'master'
git diff feature master file.txt # Show differences in file.txt between branches 'feature' and 'master'
git diff feature...master # Show changes in 'master' since 'feature' was started off of it
git diff HEAD (git commit -a) # Show changes between the working directory and the repository
git diff HEAD # Show changes between the working directory and the last commit
git diff HEAD HEAD~2 # Show differences between the last commit and two commits ago
git diff HEAD..HEAD^^ # Show differences between the last commit and two commits ago
git diff HEAD..origin/master # Show all changes on the remote compared to the local HEAD


<<COMMENT
    Compare Branches
        Show  changes between tips of branches
        Does  not change anything
COMMENT

```

```bash
git difftool -d           # Open the diff tool to compare changes in the working directory with the staging area
git difftool -d master..  # Open the diff tool to compare changes between the working directory and the master branch
```

```bash
git fetch             # Fetch remote objects and refs. Needed if new branches were added on the remote.
git fetch --unshallow # Fetch all remote branches despite a shallow clone.
git fetch -p          # Prune deleted branches from the remote repository.
git fetch -p && git branch -vv | grep ': gone]' | awk '{print $1}' | xargs git branch -D # Prune deleted branches and delete local branches that no longer exist on the remote.
git fetch [remote]    # Fetch updates from the specified remote repository.
git fetch && git merge origin/remote-branch-name # Fetch updates and merge changes from the specified remote branch.
git fetch origin      # Update the local cache of the remote repository.
git fetch origin && git branch -r # Fetch updates from the origin and list remote branches.
git fetch origin feature4  # Fetch the feature4 branch from remote to local

```

```bash
git filter-branch # Rewrite branches based on custom filters
```

```bash
git for-each-ref --sort=-committerdate refs/heads/ --format='%(committerdate) %(authorname) %(refname:short)' # List all branches sorted by the committer date in descending order, displaying the committer date, author name, and short reference name
```

```bash
git init # Initialize a new Git repository in the current folder
```

```bash
git log # Display the commit log
git log --author='Alex' --after={1.week.ago} --pretty=oneline --abbrev-commit # Show commits by 'Alex' from the past week in one line format with abbreviated commit hashes
git log --date-order --graph --tags --simplify-by-decoration --pretty=format:'%ai %h %d' # Show tags with creation dates in a graph format
git log --graph --decorate --oneline # Show commit history as a graph with decorations in one line format
git log --grep apples --oneline # Show commits with messages containing 'apples' in one line format
git log --no-merges master.. # Show commit history excluding merge commits from the master branch
git log --oneline # Show commit history in one line format
git log --patch # Show commit history with diffs
git log --pretty=format:"%h %s" --graph # Show commit history as a graph with custom format displaying abbreviated commit hash and subject
git log --stat # Show commit history with file statistics
git log -1 # Show only the most recent commit
git log -3 --oneline # Show the three most recent commits in one line format
git log -Gapples --patch # Show commits with messages containing 'apples' with diffs
git log # Display the commit log
git log # Print a list of the most recent commits
git log HEAD..origin/master --oneline # Show commit messages between the local HEAD and origin/master in one line format
git log HEAD~5..HEAD^ --online # Show commit history from five commits ago to the parent of the current HEAD in one line format
git log # List recent commits
git log nogood..master --online # Compare commits between the 'nogood' branch and the 'master' branch in one line format
```

```bash
git ls-remote # List references in a remote repository, including branches and tags
```

```bash
git merge <MYBRANCH>              # Merge the commits from the given branch into the current branch
git merge --no-ff branchname      # Merge the specified branch into the current branch, creating a merge commit even if the merge could be resolved as a fast-forward
git merge branchname              # Merge the specified branch into the current branch
git merge [branch]                # Merge the specified branch into the current branch
git merge --abort                 # Abort the merge process and try to reconstruct the pre-merge state
git merge --ff-only branchname    # Merge the specified branch into the current branch only if it can be fast-forwarded
git merge --no-ff branchname      # Merge the specified branch into the current branch, forcing a new commit even if it could be resolved as a fast-forward
git merge --squash branchname     # Merge the specified branch into the current branch, but do not create a merge commit; instead, prepare the changes to be committed
git merge branchname              # Merge the specified branch into the current branch, performing a true merge (fast-forward if possible)

git merge --abort # Stop the merge and return directory to previous state before merge started

<<COMMENT

    Merge Branches - flow
        Switch to trarget branch
        Merge source branch
        Example
            git checkout main
            git merge ticket1

    Merging Branches
        Confict
            Changes that occurred in both branches
            Git needs you to decide how to combine
        File markers indicate conflicting changes
        Edit the file to combine the content
        Add and commit to create merge commit
        Merge  commit has 2 parent commits
COMMENT
```

```bash
git mv index.html dir/index_new.html # Move the file 'index.html' to 'dir/index_new.html' and stage the change for the next commit


<<COMMENT

    the following two follows are same
        git mv old.py new.py
        or
        cy  old.py new.py
        git rm old.py
        git add new.py
COMMENT
```

```bash
git pull # Fetch from and integrate with the remote repository for the current branch
git pull # Pull from the tracked branch after the push -u command
git pull [remote] # Incorporate changes from the specified remote repository into the current branch
git pull checkout and merge remote changes in one go # This line seems incorrect; 'checkout' is not a valid argument for 'git pull'
git pull origin branchname # Fetch and merge changes from the specified branch on the remote 'origin'
git pull origin master # Pull all changes from the remote 'origin' branch
git pull origin master # Pull commits from the 'origin' remote's master branch and store them in the local repository
git pull-request # Send a pull request (this command is not a standard git command; it might be from a custom script or tool)
git pull-request -m "[comment]" -b defunkt:master -h mislav:feature # Send a pull request with a message, specifying the base and head branches
```

```bash
git push --tag # Push a single tag to the remote repository
git push --tag # You have to explicitly push tags to remotes
git push --tags # Push all tags to the remote repository
git push -f # Force push changes to the remote repository
git push -u origin --all # Push all branches to the remote repository and set upstream tracking
git push -u origin master # Push current local repository to remote. -u sets it to default for the future
git push -u origin master # Push the master branch to the remote repository and set upstream tracking
git push -u origin master # Same as above but sets 'upstream tracking' to the remote branch
git push -u origin master # Sets up tracking so that you can 'git push' without extra arguments
git push [remote] [branch] # Submit to commit the local repository to the remote repository
git push # Push changes to the remote repository
git push # Push to the tracked branch after the push -u command
git push heroku yourbranch:master # Push local branch 'yourbranch' to 'master' on the 'heroku' remote
git push heroku-staging staging:master # Push local branch 'staging' to 'master' on the 'heroku-staging' remote
git push myremote git annex copy --to myremote mybigfile # This command copies the actual content to 'myremote'
git push origin :branchname # Delete remote branch 'branchname'
git push origin branchname # Push local branch 'branchname' to the 'origin' remote
git push origin master # Push all changes to the local 'master' branch
git push origin master # Push local 'master' branch to the 'origin' remote
git push origin master # Submit to commit the master of the local repository to the master of the remote repository
git push them branch:theirbranch # Push to a contributor branch that has enabled owner edits
```

```bash
git rebase --onto <newbase> <upstream> <branch> # Rebase the current branch onto <newbase>, starting from <upstream> up to <branch>. The \ in ^ is just an escape character to make zsh play nice and is not necessary if using bash.
git rebase --abort   # Cancel the rebase operation and return to the state before rebase
git rebase -i HEAD~3 # Start an interactive rebase for the last 3 commits, allowing you to squash, edit, or reorder commits
```

```bash
git reflog                   # Show a log of all the operations (commits, checkouts, etc.) on the repository over time
git reflog refs/heads/master # Show the reflog for the 'master' branch, displaying all operations on that specific branch
```

```bash
git remote                               # Print the names of all remote repositories
git remote -v                            # List all remotes with their names and URLs
git remote -v                            # List all remotes with their URLs (verbose)
git remote -v show                       # Show the available remote repositories that have been added
git remote -v update                     # Bring remote refs up to date and show which branches were updated
git remote add <name> <remote-url>       # Add a new remote repository with the specified name and URL
git remote add name MYURL                # Add a remote repository with the name 'name' and URL 'MYURL'
git remote add origin <https://some-git-remote-url> # Add a remote repository named 'origin' with the specified URL
git remote add origin <new repo>         # Add a remote repository named 'origin' with the specified URL
git remote add origin git@example.com:example/petshop.git # Add a remote repository named 'origin' with the specified URL
git remote prune origin                  # Clean up deleted remote branches (e.g., if someone else deleted a branch on the remote)
git remote rm origin                     # Remove the remote repository named 'origin'
git remote set-branches --add origin dev # Allow setting upstream from a shallow clone for the 'dev' branch on 'origin'
git remote show origin                   # Show local-to-remote branch tracking and sync status for 'origin'
git remote update                        # Fetch from all remotes and update local refs
```

```bash
git reset --hard 073791e7dd71b90daa853b2c5acc2c925f02dbc6 # Hard reset (move HEAD and change staging directory and working directory to match the specified commit)
git reset --hard 0c6de32          # Hard reset to a specific commit, discarding all local changes
git reset --hard HEAD             # Hard reset to the latest commit of the current branch, discarding all local changes
git reset --hard HEAD             # Unstage pending changes and reset files to the state of the latest commit
git reset --hard HEAD^            # Hard reset to the previous commit, discarding the last commit and its changes
git reset --hard HEAD^            # Undo the last commit and all its changes
git reset --hard HEAD^^           # Undo the last two commits and all their changes
git reset --hard origin/master    # Undo local changes and reset to the state of the remote 'origin/master' branch
git reset --merge                 # Stop an ongoing merge (useful in case of conflicts)
git reset --mixed 073791e7dd71b90daa853b2c5acc2c925f02dbc6 # Mixed reset (move HEAD and change staging area to match the specified commit; working directory remains unchanged)
git reset --soft 073791e7dd71b90daa853b2c5acc2c925f02dbc6 # Soft reset (move HEAD only; staging area and working directory remain unchanged)
git reset --soft HEAD^            # Undo the last commit, keeping its changes in the staging area
git reset --soft HEAD^            # Undo the previous commit, keeping changes in the staging area
git reset --soft HEAD~            # Undo the latest commit, keeping changes in the staging area
git reset                         # Unstage pending changes, keeping the changes in the working directory
git reset <commit-hash>           # Reset to the specified commit, keeping changes in the working directory
git reset <FILE_OR_DIRECTORY>     # Unstage the specified file or directory
git reset filename                # Unstage the specified file
git reset HEAD index.html         # Unstage the specified file (index.html)
git reset MYFILE                  # Unstage the specified file (MYFILE) without modifying it
git reset tag                     # Unstage changes related to the specified tag



So each one affects different scopes (git reset):
https://stackoverflow.com/questions/3528245/whats-the-difference-between-git-reset-mixed-soft-and-hard
(git reset --hard ) Hard => WorkingDir + Index + HEAD
(git reset --mixed) Mixed => Index + HEAD
(git reset --soft) Soft => HEAD only (index and working dir unchanged).

Soft "pretended" to never see you have did git commit.
Mixed "pretended" to never see you have did git add .
Hard "pretended" to never see you have made file changes.

rest moves the current branch, and optionally copies data from repository to the other areas.
```

```bash
git revert HEAD                                     # Make a commit that undoes the last commit. Used to reset a commit that introduced an error or bug
git revert 073791e7dd71b90daa853b2c5acc2c925f02dbc6 # Create a new commit that undoes the changes introduced by the specified commit (073791e7dd71b90daa853b2c5acc2c925f02dbc6)
```

```bash
git rm FILE                # Remove a file from the index and the working directory. Useful if it was not gitignored.
git rm -r FOLDER           # Recursively remove a folder and its contents from the index and the working directory. Useful if it was not gitignored.
git rm filename            # Remove the specified file from the index and the working directory, stopping Git from tracking it.
git rm --cached index.html # Remove the specified file from the index but keep it in the working directory. Git will stop tracking the file.
git rm index.html          # Remove the specified file from the index and the working directory.
```

```bash
git show-branch  # Display the commit history of all branches in a visual format
```

```bash
git show                    # Display the latest commit content
git show :/^Merge           # Show the last commit whose message matches the regex 'Merge'
git show 716044             # Show the commit with the hash starting with '716044'
git show commit_id          # Show the commit with the specified commit ID
git show HEAD               # Show the latest commit on the current branch (HEAD)
git show HEAD@{"1 month ago"} # Show the state of the repository as it was 1 month ago
git show HEAD^              # Show the parent of the latest commit (HEAD^)
git show HEAD^^             # Show the grandparent of the latest commit (HEAD^^ or HEAD~2)
git show HEAD~2             # Show the grandparent of the latest commit (HEAD~2)
git show HEAD~2^2           # Show the second parent of the grandparent commit (HEAD~2^2)
git show nogood             # Show the latest commit on the branch 'nogood'
git show v1.4               # Show the tag data of the tag 'v1.4'
git show v1.4               # Show the tag data of the tag 'v1.4'
```

```bash
git stash                   # Save changes in the working directory and index to a new stash, and revert to the last commit
git stash --list            # List all stashes
git stash apply             # Apply the changes from the most recent stash to the working directory and staging area
git stash clear             # Clear the entire stash list, removing all stashes
git stash list              # List all stashes (same as 'git stash --list')
git stash pop               # Apply the changes from the most recent stash and remove it from the stash list
git stash show              # Show a high-level overview of the most recent stash
```

```bash
git status      # Print the status of the current repository, showing staged, unstaged, and untracked files
git status -uno # Show the status of the current branch without checking for changes in untracked files.
                # It also indicates if the branch is ahead, behind, or has diverged from the remote branch.


git status      # List which (unstaged) files have changed
git status      # Display a list of changed files

git status -s   # Show the working tree status in short format
git status --short # Show the working tree status in short format
    M = Modified
    A = New file added to staging area
    ?? = New file untracked by Git

```

```bash
git switch  -c branch_name # create baranch with branch_name and switch to that branch
```

```bash
git tag                                 # List all available tags
git tag -l v1.4.2.*                     # Search for tags matching the pattern 'v1.4.2.*'
git tag -a v1.4 -m 'version 1.4'        # Create an annotated tag 'v1.4' with a message 'version 1.4'
git tag -a v1.2 9fceb02                 # Tag a specific commit (9fceb02) with an annotated tag 'v1.2'
git tag v1.4                            # Create a lightweight tag 'v1.4'
git tag                                 # List all available tags
git tag -a mytag -m "I love cheesecake" # Create an annotated tag 'mytag' with a message 'I love cheesecake'
git tag dinner                          # Create a lightweight tag 'dinner'
git tag -a v1.2 9fceb02                 # Tag a specific commit (9fceb02) with an annotated tag 'v1.2'
git tag -a v0.0.3 -m 'Version 0.0.3'    # Create an annotated tag 'v0.0.3' with a message 'Version 0.0.3'
git tag                                 # List all available tags
```
