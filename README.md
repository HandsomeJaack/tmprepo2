# Instructions for fixing random push to master

## You have no devel branch or it's empty
1. Being on local _master_ create branch _devel_ if not exists
```git
git branch devel
```
2. After that rebase master on those number commits, which you accidently pushed (or you can use range of hash commits).
```git
git rebase -i HEAD~5
```
3. Now force push master, this will undo your changes on remote master.
```git
git push -f
```
4. And finally checkout on devel, push it to remote and open MR/PR, profit!
```git
git checkout devel
git push -f <remote> devel
```

## You have some commits on devel
1. Checkout on devel
```git
git checkout devel
```
2. Cherry-pick accidently added range of commits from master
```
git cherry-pick master~5..master
```
Where master~5 - means 5 commits from head and '..' is range
3. Checkout on master and repeat steps 2-4 from previous case.