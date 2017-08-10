


## Work with remote   

### Credential   
##### How to avoid being asked for password and username everytime I push?  
    git config credential.helper store
    git push https://github.com/repo.git

### Branch    
##### Fetch from remote branch  
    git checkout --track origin/daves_branch  |  git checkout -b [branch] [remotename]/[branch]

##### Change the branch name  
    git branch -m new_name

##### 


### Merge  
##### Merge all commits on issue1 branch to one commit and import it to the master branch
    git merge --squash issue1
    
### Collaboration
##### If work with others in the same branch, after each `force push`, we need to let others know and others need to do a `git reset --hard origin/branch_name` to sync with the force push. If you have any unstaged changes, make sure you stash them before doing that. If you have unpushed commit, you can do `git fetch` then `git rebase -i origin/branch_name` and only pick that unpushed commit.

##### If you want to find out who is the author of the file, try `git blame PATH_TO_THE_FILE`.

### Checkout   
##### With branch specifier only (`git checkout branch`) it will switch current working directory to specified branch, keeping local changes if possible and failing otherwise. If you already are on branch, it will do nothing at all. It only modifies files in the working directory that differ between  HEAD and branch and fails if any of them has local modifications (indexed or not).
##### With path specifier only (`git checkout .`) it writes content from index. That it is undoes unstaged local modification. To undo staged modifications, use git reset with path specifier.
##### With both branch and path specifiers (`git checkout branch .`) it writes content in specified revision. It will not modify where HEAD points, so if branch is different from HEAD, there will be staged changes afterwards. And if you have unstaged or staged changes in the previous branch, it will be gone.  

## Work locally  

### Stash   

##### Stash all changes including staged changes  
    git stash -u 
##### Stash all unstaged changes
    git stash -k 
##### Pop the last stash and remove it
    git stash pop 

### Reset  

##### Reset the HEAD to the previous commit  
    git reset --hard HEAD~
##### Reset back to the original version  
    git reset --hard ORIG_HEAD
##### Undo a commit and make the last commit to unstaged changes  
    git reset HEAD~
##### When you are one step behind the remote one, and you want to sync with it  
    git reset --hard origin/bugfix/DS-xxxx
##### When you do reset, you have 3 choices: --hard, --soft and nothing: 
    git reset --hard HEAD~ will let you go back to the previous commit, and the previous latest commit will be gone;
    git reset --soft HEAD~ will let you go back to the previous commit, and the previous latest commit will become staged changes;
    git reset HEAD~ will let you go back to the previous commit, and the previous latest commit will become unstaged changes.
    
### Rebase

##### amend to an older commit
    git rebase -i HEAD^^^
    choose the commit you want to amend, change `pick` to `edit`
    do your changes, add them, git commit --amend --no-edit
    git rebase --continue
    
##### Remove the merge commit  
    git rebase -i <sha of the commit before the diverge>
    then it will remove the merge commit

    
### Search in the history  

##### Search what happened inside a folder or a file: 
    git log -- xxx/xxx/xxx/aaa  |  git log -- xxx/xxx/xxx/abc.java
    
##### Search for a specific commit in the history.
    git log --all --grep='XXXXX'
    
    
### diff

##### git diff
    after git diff, you can save the diff file: git diff sha1 sha2 > aaa.diff
    then you can do git apply aaa.diff to add the difference to your branch
