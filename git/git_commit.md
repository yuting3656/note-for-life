# commit 

> link: `https://medium.com/@steveamaza/how-to-write-a-proper-git-commit-message-e028865e5791`

1. gti commit 
2. exit `Press Esc and then type :wq to save and exit.`


# check commit id

* git log --> 可看全部 id 

# print commit message of a given commit in git 

> link: `https://stackoverflow.com/questions/3357280/print-commit-message-of-a-given-commit-in-git`

~~~git
git log --format=%B -n 1 commit_id

git rev-list --format=%B --max-count=1 commit_id
~~~
