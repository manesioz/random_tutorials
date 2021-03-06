# Git Essentials

Configuring your git:
git config --global user.name "Zack"
git config --global user.email "zack.manesiotis@gmail.com"
git config --global color.ui true

Git has a three tree architecture: Repository, Staging, and Working. (Once you pull a file from the repo, you add it to the staging tree from the working tree, and then you commit it to the repo).
Git tracks changes buy converting the text files to some unique number via the SHA-1 hashing algorithm. HEAD is a pointer to the most recent version.

Make a folder/directory, navigate to it in cmd line
Basic Work-flow:
1. git init //initializes your git repo
2. git add . //add change set to staging tree - note: you do not have to necessarily only change one file, git considers many changes to many files as one "change set".
3. git commit -m "detailed but succinct message about commit"

Common/useful commands:
1. git log //displays commit history. You can limit the amount of commits (to top 5, for ex) by "git log -n 5". Or the time period, with "git log --since=2019-04-15" or by the author with "git log --author="Zack"" . Pro tip: press "q" when trying to exit git log
2. git status //gives overview of what tree you're on, the current directory, staging directory, and repository, and if any commits are needed
3. git reset HEAD <file> //un-stages file back to the working tree (where they are no longer tracked)
4. git diff //shows differences between what's in the repo (what HEAD is pointing at) and what's in our working directory. If multiple changes have been made to multiple files, it shows each consecutively. Note, git diff --staged does the same but with filed that are staged instead of in working directory. Again, press "q" to exit.
5. git rm <filename> //permanently removes some file, which must then be committed to the repo,
6. git mv <file_firstname> <file_secondname> //change the name of file_firstname to file_secondname
7. git mv <file> <new_folder/file> //this moves some file into a new folder
8. git checkout -- index.html //undoes a change from the working directory
9. git reset HEAD <filename> //unstages filename from the stage directory
10. git commit --amend -m "insert commit msg here" //this adds a new change to the previous commit, without making a whole new commit. Could also be used to change the commit message. *Only works with the most recent commit*
11. git commit -am "some commit msg" //this takes a file from the working directory, then adds it AND commits it in one step
12. git checkout <hash referrence to some commit> -- <filename> //this goes back to a previous commit, which is uniquely identified by the hash
13. git revert <hash referrence to some commit> //completely reverts some commit that is identified with the hash
14. git log --oneline //nice way of briefly seeing everything in the repo, there are other commands to have limit the amount of entries or the dates, etc
15. git branch <new_branch_name> //makes a new branch
16. git checkout <branch_name> //switches (changes the HEAD pointer) to the branch called branch_name
17. git branch -m <old_branch> <new_branch> // renames old_branch to new_branch
18. git branch -d <branch_to_delete> //delete a branch called branch_to_delete from the master branch
19. git merge <branch_name> //merges some branch into the master
20. git log --graph --oneline --all --decorate //this gives you a graphical representation of the master/other branches and their merges
21. git stash save "some msg" //this takes some changes in a working directory and puts it in a safe location (that is not the staging directory nor the repository)
22. git stash list //lists all things in stash, and shows what branch you were in when you made it
23. git stash -p show stash@{n} //shows the nth stash's contents
24. git stash pop stash@{n} //brings nth stash into working directory, and it removes it from stash. if you want to leave a copy in stash, use git stash apply ... (note: merge conflicts are possible)
25. git stash drop stash@{n} //removes nth stash content, or git stash clear to remove everything

Once you make a github repo, and you have a directory on your local computer, do: git remote add origin https://github.com/manesioz/some_repo.git, and then git push -u origin master (push master code to origin)