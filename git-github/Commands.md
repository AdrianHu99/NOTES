


## Work with remote   

### Fetch remote branch   
    git checkout --track origin/daves_branch  |  git checkout -b [branch] [remotename]/[branch]

### Merge  
##### Merge all commits on issue1 branch to one commit and import it to the master branch
    git merge --squash issue1
    
### Collaboration
##### If work with others in the same branch, after each `force push`, we need to let others know and others need to do a `git reset --hard HEAD` to sync with the force push

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
    
### Search in the history  

##### Search what happened inside a folder or a file: 
    git log -- xxx/xxx/xxx/aaa  |  git log -- xxx/xxx/xxx/abc.java
