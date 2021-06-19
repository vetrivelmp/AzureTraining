# How to store all the files in private repo
- Create Repo on GitLab

- Make sure to specify explicit push remte every time
```
git config --global push.default nothing
```

- Create new branch
```
git checkout -b am1
git status
```

- From .gitignote, remove few entries for files which can be stored in private repo
```
notepad .\.gitignore
```

- Add origin of private git repo and push the code to private git repo
```
git remote add gitlab-origin git@gitlab.com:atin-trainings/azure-developer-devops-data-engineer-june-21.git
git push -u gitlab-origin master
git add *
git commit -am "-"
git push -u gitlab-origin am1
git checkout master
```

- Now rename the origin name of public repo so that engineer will not git push private branch to public repo
```
git remote rename origin github-origin
git push github-origin master
git pull; git add *; git commit -am "-"; git push github-origin master
```

- Merge the change from master to am1
```
git checkout master
git merge am1
```
