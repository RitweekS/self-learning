# Git & GitHub

Welcome to the Git and GitHub crash course. Use the navigation to explore different sections on Git commands, branching, merging, and more.

## Basic Command
- To add or stage file 
```
git add
```
- To commit changes:

 ```
 git commit -m “message”
 ```
- To check if a remote repository exists or is connected:
```
git remote -v
```
- 
```
`git branch -M main`
```
- To add a remote repository:
```
git remote add origin “remote url”
```
- To push code to the remote repository (only needed the first time):
```
git push origin “remote-branch-name”
```
- To clone a repository:
```
git clone “url”
```
- To check the branches:
```
git branch
```
- To switch between branches:
```
git checkout brach_name

```
- To create a new branch:
```
git checkout -b “branch_name”

```
- To check the differences or changes between the file in the other branch and the current branch:
```
git diff branch_name_to_check
```
- To set the upstream for a branch:
```
git push -u origin branch_name_to_push

```
- To merge branches:
```
git merge branch_name_to_merge

```

## Create a New Repository from the Command Line
```
echo "# blog" >> [README.md](http://readme.md/)
git init
git add [README.md](http://readme.md/)
git commit -m "first commit"
git branch -M main
git remote add origin [https://github.com/RitweekS/blog.git](https://github.com/RitweekS/blog.git)
git push -u origin main

```

## Push an Existing Repository from the Command Line

```
git remote add origin https://github.com/RitweekS/blog.git
git branch -M main
git push -u origin main
```

## Git and Github crash course

- To add a file or to track it with Git:

```
# To add a single file
git add file.txt

# To add all files
git add .

```

- To view the differences in files from the previous commit:

```
git diff
```

- To remove a file from Git tracking:

```
git rm file.txt
```

- To commit changes:

```
git commit -m "message"
```

- To see all commits:

```
git log
```

- To see all changes in a particular commit:
```
git show commit_id
```

- To see who made changes to a file:

```
git blame filename
```

## Revert Our Changes

We have two ways to revert our code:

1. **Using `git reset`**

    ```bash
    git reset --hard commit_id
    ```
    - This command allows you to go back to any previous commit.  
    - **Drawback**: All commits made after the specified commit will be lost.

2. **Using `git revert`**

    ```bash
    git revert commit_id
    ```
    - This command reverts the changes made in a specific commit.  
    - **Advantage** : It reverts the changes without removing the commit history.

!!! Note
    If we reset the HEAD locally and want to push the reset code to GitHub forcefully, we need to consider that the HEAD on the remote repository is pointing to a different commit, while locally we have set the HEAD to another commit.

    ```
    git push -f (to push code forcefully)
    ```

## Git Branching and Remote server

- To add a remote server:
```
git remote add origin "remote url"
```
!!! note
   Here, origin is a friendly name given to the remote URL.  
    We can assign any name to it, but by convention, we use origin.


- To push code to the remote branch:
```
git push -u origin main
```
!!!Note
    Here, origin is the name given to the remote server.  
    main is the branch name.  
    The -u flag sets the upstream.  

- To push a local branch to the remote:
```
git push --set-upstream origin branch branch name
```
!!!note 
    - We can add multiple remote servers.  
    - If you have created a new branch locally that is not present on the remote, you need to run this command to push your branch with all changes to the remote.  


- To merge a remote branch into a local branch:
    
    ```
    git checkout branch_name ( branch in which we want to merge remote branch)
    
    git merge origin/branch_name
    ```
    
- To merge branches:
    There are two ways to merge branches:
    - Using the merge command:
        This command combines the entire branch into a single commit, which is then merged into the target branch. This approach loses the history of individual commits, as only one merge commit is added to the specified branch.
                    
            ```
            git merge branch_name
            ```
            
    - Using rebase:
       Rebase also merges branches but differs from the merge command. It attaches all commits to the head of the branch where you want to merge your code, preserving the commit history.
        
        ```
        git rebase branch_name ( what we want to merge )
        ```
        

- Git stash
    - It is used to temporarily save changes.
    - When you need to pull code from the remote repository but have local changes you don't want to commit yet, you can stash your current changes and then pull the code. After that, you can retrieve the stashed changes.
        
        In this situation we can stash our current changes and then pull the code , and after that we can again get the code from stash .
        ```
        // to stash current changes
        git stash
        
        //to get back the stash chanegs
        git stash apply
        ```