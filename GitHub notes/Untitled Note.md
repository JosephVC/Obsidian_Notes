---
---
**General github notes**

if you have to re-clone a repo, you will have to re-connect it with github to make sure github sees it - same if you are connecting to heroku

if you are within a poetry shell and do a git comm/git push, it won't show up in your repo online; **you'll  need to exit the shell and commit/push from there**

**branch commits that don't show up automatically to be merged**: if you need to merge commits from non-main branches, then 

1. go to the repo main page
2. do a pull request
3. check your branches against the main branch to see if anything needs merging
4. the reason the new commit didn't automatically show up at the top of the repo's main page is likely due to some conflict
