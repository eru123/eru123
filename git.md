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

3. Store git credentials on Ubuntu
```bash
git config --global credential.helper store
```

4. check global config

```bash
git config --global --list
```

read: [reference](https://docs.gitlab.com/ee/gitlab-basics/start-using-git.html)

### Delete git repo on local Machine

 - Windows

```bash
attrib -h -r -s /s /d <repo_folder>
rmdir /s /q <repo_folder>
```

 - Linux

```bash
rm -rf <repo_folder>
```

read: [windows reference](https://stackoverflow.com/questions/17369850/how-to-remove-git-repository-created-on-desktop), [linux reference](https://www.geeksforgeeks.org/deleting-a-local-github-repository/)

### Git submodules

1. Add a submodule

```bash
git submodule add <repo_url> <submodule_path>
```

2. Update or pull a submodule

```bash
git submodule update --remote
git submodule update
```

3. Delete a submodule

 - Windows

```bash
git submodule deinit <submodule_path>
git rm <submodule_path>
git commit-m "remove: submodule"
attrib -h -r -s /s /d .git/modules/<submodule_path>
rmdir /s /q .git/modules/<submodule_path>
```

 - Linux

```bash
git submodule deinit <submodule_path>
git rm <submodule_path>
git commit-m "remove: submodule"
rm -rf .git/modules/<path_to_submodule>
```

4. Clone a git repo including it's submodules

```bash
git clone --recurse-submodules --remote-submodules -j8 <repo_url>
```

read: [submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules), [delete submodule](https://gist.github.com/myusuf3/7f645819ded92bda6677), [clone repo with submodules](https://stackoverflow.com/questions/3796927/how-to-git-clone-including-submodules)
