npx jest  ( to start the test )


To make a new branch  ( make sure there are some kind of file change )
```md
git add .
git checkout -b my-new-branch
git commit -am 'initial workflow for testing'
git status
git push origin my-new-branch
```
If the new branch test passes then it can be merged.
Otherwise, the person reviewing the code can add a note on what needs to be fixed.
After fixing the code, do this and resubmit:

```md
git commit -am 'fixing broken code'
git push origin my-new-branch
```

To delete a branch
```md
git checkout main   ( first switch to a different branch )
git branch -d my-second-branch   ( delete )
git branch -D my-second-branch   ( force delete - if delete doesn't work )
```