# statsh usage

1. 新增一 stash 
- git stash save -u [檔案]

~~~git
D:\HyWeb\Project\Note\git>git stash save -u git_stash
Saved working directory and index state On master: git_stash
~~~

2. 看 statsh list
- git stash list

~~~git 
D:\HyWeb\Project\Note\git>git stash list
stash@{0}: On master: git_stash
~~~

3. 把 stash 檔案加回來
- git stash apply [stash@{檔案數字}]

~~~git
D:\HyWeb\Project\Note\git>git stash apply stash@{0}
Already up to date!
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        git_stash.md

nothing added to commit but untracked files present (use "git add" to track)
~~~

4. 把 stash 檔案刪除
- git stash drop [stash@{檔案數字}]

~~~git
D:\HyWeb\Project\Note\git>git stash drop stash@{0}
Dropped stash@{0} (af78ea50cfc846d37278f899fce4c3f25d302191)
~~~