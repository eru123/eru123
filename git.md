# Git Shortcuts

### Configure Git
1. add username
```bash
git config --global user.name "eru123"
```

2. add email
```bash
git config --global user.email "yeoligoakino@gmail.com"
```
3. check global config
```bash
git config --global --list
```
read: [reference](https://docs.gitlab.com/ee/gitlab-basics/start-using-git.html)

### Delete git repo on local Machine

 - Windows
```bash
attrib -h -r -s /s /d repo_folder
rmdir /s /q repo_folder
```

 - Linux

```bash
rm -rf repo_folder
```

read: [windows reference](https://stackoverflow.com/questions/17369850/how-to-remove-git-repository-created-on-desktop), [linux reference](https://www.geeksforgeeks.org/deleting-a-local-github-repository/)