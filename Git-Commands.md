# Git Instructions:

## Create a new project:
  ```
  rails new <repo_name> -T
  ```

  1. Sign into your GitHub account.
  2. Create a new repo named <repo_name>
  3. Go back to git and do the following:

  ```
  git init
  git add .
  git commit -m 'First commit and README update'
  git remote add origin git@github.com:<user name>/<repo_name>.git
  git push -u origin master
  ```
  *Note: If you don't use the above command the `git push` commands later will not work.*

## Before Each New Checkpoint:
  ```
  git status
  git checkout -b <new_branch_name>
  ```

## To push a commit (backup your work) before the end of the checkpoint:
  ```
  git status
  git add .
  git status
  git commit -m "Notes on project"
  git push origin <branch_name>
  ```
  *Now you resume working as you were before*

## After Each New Checkpoint:
  ```
  git status
  git add .
  git status
  git commit -m "Notes on project"
  git push origin <branch_name>
  git checkout master
  git merge <branch_name>
  git push
  ```

## Before Each Assignment:
  ```
  git status
  git checkout -b <new_branch_name>
  ```

## After Each Assignment:
  ```
  git status
  git add .
  git status
  git commit -m "Assignment notes"
  git push origin <branch_name>
  git checkout master
  ```

## Add a single file to the repo:
  ```
  git add <directory and file name>
  ```
  _ex: git add app/controllers/test_file.rb_

## Remove a file from the commit:
  ```
  git rm <filename>
  ```
  _ex: git rm app/controllers/test_file.rb_

## Remove a file from the commit even if changes have been made:
  ```
  git rm -f <filename>
  ```
  _ex: git rm -f log/test.log_

## Create an alias to speed up work
  ```
  git config --global alias.<alias word> <Git action word>
  ```
  _ex: git config --global alias.co checkout_
  _makes "git co" mean the same thing as "git checkout"_

## Clone an existing Github project:
  1. Command Prompt:
      1. Navigate to Rails folder
  2.  Web Browser:
      1. Go to github.com
      2. copy the SSH link from repo.
      3. Navigate to it and select "SSH clone URL"
      4. Copy this to your clipboard.
      3.  Command Prompt:
      1. Enter the following into the command prompt:
      2. git clone <text-from-clipboard>

## How to clone a specific branch in git
  ```
  git clone -b <branch> <SSH link from repo>
  ```
  ex: git clone -b develop git@github.com:user/myproject.git

## Edit a commit message:
  ```
  git checkout <branch_with_commit_message_to_be_edited>
  If commit has not been pushed to Github
    git commit --amend -m "New commit message"
  --
  If commit has been pushed to Github
    git commit --amend - "New commit message"
    git push <remote> <branch> --force
  ```
      Warning: force-pushing will overwrite the remote branch.

## Move between branches:
  ```
  git checkout <branch_name>
  ```

## Rename local branch:
  ```
  git branch -m <oldname> <newname>
  ```

## If working from wrong branch:
  ```
  git stash
  git checkout <branch_name>
  git stash apply
  ```

## Load and run/view site from earlier commits:
  ```
  git checkout <sha1-of-commit>
  ```

## Create a new branch from earlier commit:
  ```
  git checkout -b branchname <sha1-of-commit>
  ```
  ex: git checkout -b install-node-modules 4abc90b810249j25bc0481c89612d00dlcd2a91e

## Delete Branch:
  ```
  git branch -D <branch_name>
  ```

## Revert one specific file to state of last commit:
  ```
  git checkout -- <file location and name i.e. db/schema.rb>
  ```

## Revert all files to a previous commit:
  ```
  git reset --hard <old-commit-id>
  git push -f <remote-name> <branch-name>
  ```
  _**Note:** Using this is dangerous in a collaborative environment: you're rewriting history_

## List all branches:
  ```
  git branch
  ```

## List all branches with commits:
  ```
  git show-branch
  ```

## Add Version numbers:
  ```
  git tag <version number> <commit id>
  ```

## Have Git autocomplete branch names on a Mac:
  1. Copy file below to _~/ directory_. **https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash**

  2. Add following line to _~/.bashrc_ file:  **source ~/.git-completion.bash**

  3. Find the _.bash_profile_ file and add:
  ```
  if [ -s ~/.bashrc ]; then source ~/.bashrc; fi
  ```

  *Instant Happiness if you use long descriptive branch names*

  *Thanks to [Jack Schuss](https://github.com/yakschuss) for this one.*

## How to re-enable ability to commit after changing repo URL:
  ```
  git remote set-url origin <SSH link from repo>
  ```
  ex: git remote set-url origin git@github.com:user/myproject.git
  
## How to ignore file after it's already been committed:
  Edit `.gitignore` to match the file you want to ignore
  ```
  git rm --cached /path/to/file
  ```
  ex: git rm --cached config/database.yml

## How to reconnect VSC to GitHub
  In case your token expires or you receive a "failed to authenticate to git remote" message.
  Go to:
  ```
  https://github.com/settings/apps
  ```
  Choose your token type.
  Choose the token security settings appropriate for your needs.
  Copy your token.
  Go to your Terminal in VSC and enter:
  ```
  git remote set-url origin https://<TOKEN>@github.com/<user_name or organization_name>/<repo_name>.git
  ```
  ### If you receive a "remote repository not found" error:
  Redo previous code with your username, not your email address.
  Yes, I made this mistake.
