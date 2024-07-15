npx jest  ( to start the test )


To make a new branch  ( make sure there are some kind of file change )
```md
git add .
git checkout -b my-second-branch
git commit -am 'initial workflow for testing'
git status
git push origin my-second-branch
```
 
To delete a branch
```md
git checkout main   ( first switch to a different branch )
git branch -d my-second-branch   ( delete )
git branch -D my-second-branch   ( force delete - if delete doesn't work )
```