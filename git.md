# Git useful Linux command line

## how to update git submodule values e.g url

```bash
# check the list
git config -f .gitmodules --list

# update a url
# find you
# - repo name
# - group name (if you have any, optional)
# - repo name at the end
git config -f .gitmodules --replace-all submodule.<repo-name>.url git@git.example.com:<group-name/repo-name>.git

# check it
 git config -f .gitmodules --get  submodule.<repo-name>.url
```
