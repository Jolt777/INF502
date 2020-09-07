# Assignment 2: Git/GitHub Assignment

#### Name: Jolten Larrermore
#### Instructor: Dr. Igor Steinmacher
#### Course: INF502
#### Date: September 8, 2020

## Part 1: Dealing with git

1. Describe what is the output of the following commands
    - `git branch`
    - `git checkout BRANCH_NAME (USE THE NAME OF AN EXISTING BRANCH)`
    - `git log --decorate`

```
joltenlarremore@Joltens-MacBook-Pro ~ % cd handson/
joltenlarremore@Joltens-MacBook-Pro handson % git branch
* master
  math
joltenlarremore@Joltens-MacBook-Pro handson % git checkout master
Already on 'master'
joltenlarremore@Joltens-MacBook-Pro handson % git checkout math
Switched to branch 'math'
joltenlarremore@Joltens-MacBook-Pro handson % git branch
  master
* math
joltenlarremore@Joltens-MacBook-Pro handson % git log --decorate
commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e (HEAD -> math)
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:13:48 2019 -0700

    Adding some more knowledge to the function

commit 654b490a181dedf82dd6deda5f9848d6cca05918
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:12:14 2019 -0700

    Added a draft of A.py

commit 2dfb02c3f9383d6c3b2695c99e175d8b85f594a1
Author: Igor Steinmacher <igorsteinmacher@gmail.com>
Date:   Wed Aug 14 23:08:47 2019 -0700

     Creating all files (all empty)
```

#### Student's Notes
- The `git branch` command lets you list the branches.
- The `git checkout BRANCH_NAME` command lets you switch from a current branch to a different branch.
- The `git log` command shows commit logs. The `--decorate` flag allows git to print out the reference names (i.e. the author) of any commits that are shown. The `decorate` flag can also show the dates on which the commits are created.

2. Try `git log --graph --all`. What do you see?

```
joltenlarremore@Joltens-MacBook-Pro handson % git log --graph --all
* commit 18931d12a8be7cac049b73c6bc8136e9482f3371 (master)
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:15:28 2019 -0700
| 
|     Making a small change here
|   
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e (HEAD -> math)
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:13:48 2019 -0700
|   
|       Adding some more knowledge to the function
| 
* commit 654b490a181dedf82dd6deda5f9848d6cca05918
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:12:14 2019 -0700
| 
|     Added a draft of A.py
| 
* commit 2dfb02c3f9383d6c3b2695c99e175d8b85f594a1
  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
  Date:   Wed Aug 14 23:08:47 2019 -0700
  
       Creating all files (all empty)
:...skipping...
* commit 18931d12a8be7cac049b73c6bc8136e9482f3371 (master)
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:15:28 2019 -0700
| 
|     Making a small change here
|   
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e (HEAD -> math)
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:13:48 2019 -0700
|   
|       Adding some more knowledge to the function
| 
* commit 654b490a181dedf82dd6deda5f9848d6cca05918
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:12:14 2019 -0700
| 
|     Added a draft of A.py
| 
* commit 2dfb02c3f9383d6c3b2695c99e175d8b85f594a1
  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
  Date:   Wed Aug 14 23:08:47 2019 -0700
  
       Creating all files (all empty)
~
```
#### Student's Notes
- The `--graph` flag in the `git log` command allows git to draw a text-based graphical representation of the commit history. Upon closer examination, the graph history is shown as a series of actions; each one is printed in between the commits.
- The `--all` flag in the `git log` command asks git for the logs of all references, basically the branches and the tags.

3. Use `git diff BRANCH_Name` to view the differences from a branch and the current branch. 
Summarize the difference from master to the other branch.

```
joltenlarremore@Joltens-MacBook-Pro handson % git diff master
diff --git a/A.py b/A.py
index dc1e9bd..0afa98c 100644
--- a/A.py
+++ b/A.py
@@ -1,3 +1,11 @@
 #this is just an example, do not freak out
 def calculate_this(operator, num1, num2):
-   print 'my knowledge is limited'     
+   if operator == 'sum':
+      print num1 + num2
+      print 'That was easy buddy'
+   else:
+      if operator == 'subtraction':
+         print num1 - num2
+         print 'I could handle that...'
+      else:
+         print 'my knowledge is limited'
diff --git a/B.py b/B.py
index c63f94c..e69de29 100644
--- a/B.py
+++ b/B.py
@@ -1 +0,0 @@
-# Another file that will receive a line of code... at least.
joltenlarremore@Joltens-MacBook-Pro handson % git checkout master
Switched to branch 'master'
joltenlarremore@Joltens-MacBook-Pro handson % git diff math
diff --git a/A.py b/A.py
index 0afa98c..dc1e9bd 100644
--- a/A.py
+++ b/A.py
@@ -1,11 +1,3 @@
 #this is just an example, do not freak out
 def calculate_this(operator, num1, num2):
-   if operator == 'sum':
-      print num1 + num2
-      print 'That was easy buddy'
-   else:
-      if operator == 'subtraction':
-         print num1 - num2
-         print 'I could handle that...'
-      else:
-         print 'my knowledge is limited'
+   print 'my knowledge is limited'     
diff --git a/B.py b/B.py
index e69de29..c63f94c 100644
--- a/B.py
+++ b/B.py
@@ -0,0 +1 @@
+# Another file that will receive a line of code... at least.
joltenlarremore@Joltens-MacBook-Pro handson % 
```

#### Student's Notes
Git is using a color code in order to display the differences done between the two branches: lines in green ("+") are lines added to the files/branches/etc., and lines in red ("-") are the ones that are deleted from the files/branches/etc. As shown above, both branches have the function `calculate_this()` defined, as well as the comment, `#this is just an example, do not freak out`. When viewed closely, the `master` branch contains the if-else conditional statements within the function. In comparison, the `math` branch doesn't contain the conditional statements, but has the the extra `print` function that prints out 'my knowledge is limited', as well as the comment `#Another file that will receive a line of code... at least`. These notable features in the `math` branch is missing in the `master` branch.

4. Write a command sequence to merge the non-master branch into `master`

```
joltenlarremore@Joltens-MacBook-Pro handson % git branch
* master
  math
joltenlarremore@Joltens-MacBook-Pro handson % git merge math
hint: Waiting for your editor to close the file... 






Merge made by the 'recursive' strategy.
 A.py | 10 +++++++++-
 1 file changed, 9 insertions(+), 1 deletion(-)
joltenlarremore@Joltens-MacBook-Pro handson % git branch
* master
  math
joltenlarremore@Joltens-MacBook-Pro handson % 
```

5. Write a command (or sequence) to (i) create a new branch called `math` (from the `master`) and
(ii) change to this branch

```
joltenlarremore@Joltens-MBP handson % git branch
* master
  math
joltenlarremore@Joltens-MBP handson % git branch -d math
Deleted branch math (was e3c629d).
joltenlarremore@Joltens-MBP handson % git branch
* master
joltenlarremore@Joltens-MBP handson % git checkout -b math master
Switched to a new branch 'math'
joltenlarremore@Joltens-MBP handson % git branch
  master
* math
joltenlarremore@Joltens-MBP handson % 
```

#### Student's Notes
- `git branch -d BRANCH_NAME` allows git to delete a particular branch
- `git checkout -b <NEW_BRANCH> <EXISTING_BRANCH>` allows git to create a new branch (i.e. `math`) from the existing branch (i.e. `master`), and then check outs the new branch. The `-b` option allows the following steps to occur in that order.

6. Edit B.py adding the following source code below the content you have there

```
print 'I know math, look:'
print 2+2
```

Status: **complete**

#### Student's Notes
I used `nano` to edit the python file

7. Write a command (or sequence) to commit your changes

```
Last login: Sun Sep  6 10:53:25 on console
joltenlarremore@Joltens-MBP ~ % cd handson
joltenlarremore@Joltens-MBP handson % ls
A.py	B.py
joltenlarremore@Joltens-MBP handson % git branch
  master
* math
joltenlarremore@Joltens-MBP handson % nano B.py
joltenlarremore@Joltens-MBP handson % git commit B.py -m "Adding two print functions; one is a statement of declaration on having knowledge of math, and the other is a math equation"
[math 6b74cf2] Adding two print functions; one is a statement of declaration on having knowledge of math, and the other is a math equation
 Committer: Jolten Larremore <joltenlarremore@Joltens-MBP.PK5001Z>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 1 file changed, 2 insertions(+)
joltenlarremore@Joltens-MBP handson % git status
On branch math
nothing to commit, working tree clean
joltenlarremore@Joltens-MBP handson % git log --graph --all
* commit 6b74cf2c802429651b2d3496cb544f1b1613e021 (HEAD -> math)
| Author: Jolten Larremore <joltenlarremore@Joltens-MBP.PK5001Z>
| Date:   Sun Sep 6 12:08:06 2020 -0700
| 
|     Adding two print functions; one is a statement of declaration on having knowledge of math, and the other is a math equation
|   
*   commit 527e9a9bbed8e216d8a3843758616d678e6303dc (master)
|\  Merge: 18931d1 e3c629d
| | Author: Jolten Larremore <joltenlarremore@Joltens-MacBook-Pro.local>
| | Date:   Fri Sep 4 15:46:43 2020 -0700
| | 
| |     Merge branch 'math' into master
| | 
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e
| | Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| | Date:   Wed Aug 14 23:13:48 2019 -0700
| | 
| |     Adding some more knowledge to the function
| | 
* | commit 18931d12a8be7cac049b73c6bc8136e9482f3371
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:15:28 2019 -0700
|   
:...skipping...
* commit 6b74cf2c802429651b2d3496cb544f1b1613e021 (HEAD -> math)
| Author: Jolten Larremore <joltenlarremore@Joltens-MBP.PK5001Z>
| Date:   Sun Sep 6 12:08:06 2020 -0700
| 
|     Adding two print functions; one is a statement of declaration on having knowledge of math, and the other is a math equation
|   
*   commit 527e9a9bbed8e216d8a3843758616d678e6303dc (master)
|\  Merge: 18931d1 e3c629d
| | Author: Jolten Larremore <joltenlarremore@Joltens-MacBook-Pro.local>
| | Date:   Fri Sep 4 15:46:43 2020 -0700
| | 
| |     Merge branch 'math' into master
| | 
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e
| | Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| | Date:   Wed Aug 14 23:13:48 2019 -0700
| | 
| |     Adding some more knowledge to the function
| | 
* | commit 18931d12a8be7cac049b73c6bc8136e9482f3371
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:15:28 2019 -0700
|   
|       Making a small change here
:...skipping...
* commit 6b74cf2c802429651b2d3496cb544f1b1613e021 (HEAD -> math)
| Author: Jolten Larremore <joltenlarremore@Joltens-MBP.PK5001Z>
| Date:   Sun Sep 6 12:08:06 2020 -0700
| 
|     Adding two print functions; one is a statement of declaration on having knowledge of math, and the other is a math equation
|   
*   commit 527e9a9bbed8e216d8a3843758616d678e6303dc (master)
|\  Merge: 18931d1 e3c629d
| | Author: Jolten Larremore <joltenlarremore@Joltens-MacBook-Pro.local>
| | Date:   Fri Sep 4 15:46:43 2020 -0700
| | 
| |     Merge branch 'math' into master
| | 
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e
| | Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| | Date:   Wed Aug 14 23:13:48 2019 -0700
| | 
| |     Adding some more knowledge to the function
| | 
* | commit 18931d12a8be7cac049b73c6bc8136e9482f3371
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:15:28 2019 -0700
|   
|       Making a small change here
| 
:...skipping...
* commit 6b74cf2c802429651b2d3496cb544f1b1613e021 (HEAD -> math)
| Author: Jolten Larremore <joltenlarremore@Joltens-MBP.PK5001Z>
| Date:   Sun Sep 6 12:08:06 2020 -0700
| 
|     Adding two print functions; one is a statement of declaration on having knowledge of math, and the other is a math equation
|   
*   commit 527e9a9bbed8e216d8a3843758616d678e6303dc (master)
|\  Merge: 18931d1 e3c629d
| | Author: Jolten Larremore <joltenlarremore@Joltens-MacBook-Pro.local>
| | Date:   Fri Sep 4 15:46:43 2020 -0700
| | 
| |     Merge branch 'math' into master
| | 
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e
| | Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| | Date:   Wed Aug 14 23:13:48 2019 -0700
| | 
| |     Adding some more knowledge to the function
| | 
* | commit 18931d12a8be7cac049b73c6bc8136e9482f3371
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:15:28 2019 -0700
|   
|       Making a small change here
| 
* commit 654b490a181dedf82dd6deda5f9848d6cca05918
:...skipping...
* commit 6b74cf2c802429651b2d3496cb544f1b1613e021 (HEAD -> math)
| Author: Jolten Larremore <joltenlarremore@Joltens-MBP.PK5001Z>
| Date:   Sun Sep 6 12:08:06 2020 -0700
| 
|     Adding two print functions; one is a statement of declaration on having knowledge of math, and the other is a math equation
|   
*   commit 527e9a9bbed8e216d8a3843758616d678e6303dc (master)
|\  Merge: 18931d1 e3c629d
| | Author: Jolten Larremore <joltenlarremore@Joltens-MacBook-Pro.local>
| | Date:   Fri Sep 4 15:46:43 2020 -0700
| | 
| |     Merge branch 'math' into master
| | 
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e
| | Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| | Date:   Wed Aug 14 23:13:48 2019 -0700
| | 
| |     Adding some more knowledge to the function
| | 
* | commit 18931d12a8be7cac049b73c6bc8136e9482f3371
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:15:28 2019 -0700
|   
|       Making a small change here
| 
* commit 654b490a181dedf82dd6deda5f9848d6cca05918
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:12:14 2019 -0700
| 
:...skipping...
* commit 6b74cf2c802429651b2d3496cb544f1b1613e021 (HEAD -> math)
| Author: Jolten Larremore <joltenlarremore@Joltens-MBP.PK5001Z>
| Date:   Sun Sep 6 12:08:06 2020 -0700
| 
|     Adding two print functions; one is a statement of declaration on having knowledge of math, and the other is a math equation
|   
*   commit 527e9a9bbed8e216d8a3843758616d678e6303dc (master)
|\  Merge: 18931d1 e3c629d
| | Author: Jolten Larremore <joltenlarremore@Joltens-MacBook-Pro.local>
| | Date:   Fri Sep 4 15:46:43 2020 -0700
| | 
| |     Merge branch 'math' into master
| | 
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e
| | Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| | Date:   Wed Aug 14 23:13:48 2019 -0700
| | 
| |     Adding some more knowledge to the function
| | 
* | commit 18931d12a8be7cac049b73c6bc8136e9482f3371
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:15:28 2019 -0700
|   
|       Making a small change here
| 
* commit 654b490a181dedf82dd6deda5f9848d6cca05918
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:12:14 2019 -0700
| 
|     Added a draft of A.py
| 
:...skipping...
* commit 6b74cf2c802429651b2d3496cb544f1b1613e021 (HEAD -> math)
| Author: Jolten Larremore <joltenlarremore@Joltens-MBP.PK5001Z>
| Date:   Sun Sep 6 12:08:06 2020 -0700
| 
|     Adding two print functions; one is a statement of declaration on having knowledge of math, and the other is a math equation
|   
*   commit 527e9a9bbed8e216d8a3843758616d678e6303dc (master)
|\  Merge: 18931d1 e3c629d
| | Author: Jolten Larremore <joltenlarremore@Joltens-MacBook-Pro.local>
| | Date:   Fri Sep 4 15:46:43 2020 -0700
| | 
| |     Merge branch 'math' into master
| | 
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e
| | Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| | Date:   Wed Aug 14 23:13:48 2019 -0700
| | 
| |     Adding some more knowledge to the function
| | 
* | commit 18931d12a8be7cac049b73c6bc8136e9482f3371
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:15:28 2019 -0700
|   
|       Making a small change here
| 
* commit 654b490a181dedf82dd6deda5f9848d6cca05918
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:12:14 2019 -0700
| 
|     Added a draft of A.py
| 
* commit 2dfb02c3f9383d6c3b2695c99e175d8b85f594a1
  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
  Date:   Wed Aug 14 23:08:47 2019 -0700
  
       Creating all files (all empty)
~
joltenlarremore@Joltens-MBP handson % 
```
#### Student's Notes
- `git commit <FILE_NAME> -m <COMMIT>` allows git to commit on the changes made by the user. The `-m` flag is for the message on the commit.
- `git status` checks the status on the selected branch.
- `git log --graph --all` is utilized to check if the recently-made commit is successfully implemented.

8. Change back to the `master` branch and change B.py adding the following source code
(commit your change to `master`):

```
joltenlarremore@Joltens-MBP handson % git branch
  master
* math
joltenlarremore@Joltens-MBP handson % git checkout master
Switched to branch 'master'
joltenlarremore@Joltens-MBP handson % git branch
* master
  math
joltenlarremore@Joltens-MBP handson % nano B.py
joltenlarremore@Joltens-MBP handson % git commit -m "Add a new line in B.py" 
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   B.py

no changes added to commit (use "git add" and/or "git commit -a")
joltenlarremore@Joltens-MBP handson % git commit -a -m "Add a new line to B.py"
[master 13ea041] Add a new line to B.py
 Committer: Jolten Larremore <joltenlarremore@Joltens-MBP.PK5001Z>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 1 file changed, 1 insertion(+)
joltenlarremore@Joltens-MBP handson % 
```

9. Write a command sequence to merge the `math` branch into `master` and describe what
happened

```
joltenlarremore@Joltens-MBP handson % git checkout math
Switched to branch 'math'
joltenlarremore@Joltens-MBP handson % git merge master
Auto-merging B.py
CONFLICT (content): Merge conflict in B.py
Automatic merge failed; fix conflicts and then commit the result.
joltenlarremore@Joltens-MBP handson % 
```
#### Student's Notes
When I tried to merge the `math` branch into the `master` branch, a merge conflict is detected. Merge conflicts can happen when the user command git to merge branches that have competing commits. If git detected a merge conflict, then it will tell the user that the automatic merge has failed. It means that git doesn't know what to do, and is asking the user to fix the conflicts. Also, the user needs to commit on the result.

10. Write a set of commands to abort the merge

```
joltenlarremore@Joltens-MBP handson % git merge --abort
```

11. Now repeat item 9, but proceed with the manual merge (Editing B.py). All implemented
functions are needed. Explain your procedure

```
joltenlarremore@Joltens-MBP handson % git merge master
Auto-merging B.py
CONFLICT (content): Merge conflict in B.py
Automatic merge failed; fix conflicts and then commit the result.
joltenlarremore@Joltens-MBP handson % git status
On branch math
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
	both modified:   B.py

no changes added to commit (use "git add" and/or "git commit -a")
joltenlarremore@Joltens-MBP handson % nano B.py
joltenlarremore@Joltens-MBP handson % cat B.py
# Another file that will receive a line of code... at least.
print 'I know math, look:'
print 2+2
print 'hello world!'
joltenlarremore@Joltens-MBP handson % git add B.py
joltenlarremore@Joltens-MBP handson % git status
On branch math
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:
	modified:   B.py

joltenlarremore@Joltens-MBP handson % git commit
[math 2c58b97] Merge branch 'master' into math
 Committer: Jolten Larremore <joltenlarremore@Joltens-MBP.PK5001Z>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

joltenlarremore@Joltens-MBP handson % 
```

#### Procedures
- First, checkout to `math` branch, and type in `git merge master` to start the manual merge of the math branch into the master branch
- Second, type `git status` to display the state of the working directory and the staging area. Upon executing the command, git tells the user that there are unmerged paths on the branch `math`, as well as giving out a few vital commands to fix the conflicts and complete the merge.
- Third, use `nano` on the file `B.py` to edit the file by deleting all conflict markers: `<<<<<<< HEAD`, `=======`, `>>>>>>> BRANCH_NAME`
- Next, type `cat B.py` to view the contents of B.py on the standard output. This is to check to see if the disired changes made on the file has been made (i.e. no conflict markers).
- Then, type `git add B.py` to mark the resolution. In other words, add the `B.py` file to the index.
- After that step, type `git status` agian to make sure that the changes are committed, and all conflicts are fixed.
- Finally, type `git commit` to finalized the merge.

12. Write a command (or set of commands) to proceed with the merge and make `master` branch
up-to-date

```
joltenlarremore@Joltens-MBP handson % git branch
  master
* math
joltenlarremore@Joltens-MBP handson % git checkout master
Switched to branch 'master'
joltenlarremore@Joltens-MBP handson % git branch
* master
  math
joltenlarremore@Joltens-MBP handson % git status
On branch master
nothing to commit, working tree clean
joltenlarremore@Joltens-MBP handson % git log --graph --all
*   commit 2c58b97d5016d6b09475d87e7820896ff53a9812 (math)
|\  Merge: 6b74cf2 13ea041
| | Author: Jolten Larremore <joltenlarremore@Joltens-MBP.PK5001Z>
| | Date:   Sun Sep 6 17:07:08 2020 -0700
| | 
| |     Merge branch 'master' into math
| | 
| * commit 13ea0415674ecef33de5fec8140a01141b3e3639 (HEAD -> master)
| | Author: Jolten Larremore <joltenlarremore@Joltens-MBP.PK5001Z>
| | Date:   Sun Sep 6 13:49:11 2020 -0700
| | 
| |     Add a new line to B.py
| | 
* | commit 6b74cf2c802429651b2d3496cb544f1b1613e021
|/  Author: Jolten Larremore <joltenlarremore@Joltens-MBP.PK5001Z>
|   Date:   Sun Sep 6 12:08:06 2020 -0700
|   
|       Adding two print functions; one is a statement of declaration on having knowledge of math, and the other is a math equation
|   
*   commit 527e9a9bbed8e216d8a3843758616d678e6303dc
|\  Merge: 18931d1 e3c629d
| | Author: Jolten Larremore <joltenlarremore@Joltens-MacBook-Pro.local>
| | Date:   Fri Sep 4 15:46:43 2020 -0700
| | 
| |     Merge branch 'math' into master
| | 
| * commit e3c629dd524712aedea96d7dbaad1c50d12b5b5e
| | Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| | Date:   Wed Aug 14 23:13:48 2019 -0700
| | 
| |     Adding some more knowledge to the function
| | 
* | commit 18931d12a8be7cac049b73c6bc8136e9482f3371
|/  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
|   Date:   Wed Aug 14 23:15:28 2019 -0700
|   
|       Making a small change here
| 
* commit 654b490a181dedf82dd6deda5f9848d6cca05918
| Author: Igor Steinmacher <igorsteinmacher@gmail.com>
| Date:   Wed Aug 14 23:12:14 2019 -0700
| 
|     Added a draft of A.py
| 
* commit 2dfb02c3f9383d6c3b2695c99e175d8b85f594a1
  Author: Igor Steinmacher <igorsteinmacher@gmail.com>
  Date:   Wed Aug 14 23:08:47 2019 -0700
  
       Creating all files (all empty)
joltenlarremore@Joltens-MBP handson %         
```

#### Student's Notes
- The merge is already explained upon answering the previous question (#11)
- When executing the command `git status`, the ideal message shown is `nothing to commit, working tree clean`. This means that all the files in the current repo are being managed by git, and the most recent version of the file has been committed.

## Part 2: Using GitHub

1. Into the students folder, create a file called LASTNAME_FIRSTNAME.md (please change
LASTNAME_FIRSTNAME for your actual last and first names).
2. Use Markdown to structure the following information about the last paper you've read (you can
structure your markdown the way you want):
- Title
- Venue (journal name/conference)
- Number of pages
- 3 outcomes of the paper
- link to the paper online
3. Send your file back to this repository until creating a pull request.
4. Report your experience of making this submission, including the steps followed, commands
used, and hurdles faced (within the file you create for **part 1**)

```
To sum up my experience of this part of the assignment, I have to say that it's not really that bad. In my honest opinion, I was expecting it to be challenging, but it's really a cake walk. In other words, I encountered no hurdles in completing this part of the assignment. Here are the procedures that I took in order to see a successful submission:
1. On GitHub, in a repository titled 'igorsteinmacher/INF502-Fall2020', I click on the student's folder to enter.
2. Inside the student's folder, I create a file called 'Larremore_Jolten.md'.
3. During the creation of the file using markdown, I have it structured it to include the following information about the last paper that I read. I decided to use a research paper titled "The Evolution of Human Cancer Gene Duplication across Mammals", written by Marc Tollis, Aika K. Schneider-Utaka, and Carlo C. Maley.
The following is a list of commands/formatting changes, etc. made in the creation of the Markdown file:
	* For the title, I used the <h1> tag (#) to make it appear in big, bold letters.
	* For the venue (journal name/conference), I first use the bold command (**TEXT**) on the subtitle "Venue (Journal Name/Conference):". After a single space from the subtile, I typed in the name of the journal that this paper is published under, and that is "Molecular Biology and Evolution". Then on a new line below the subtitle, I pressed *tab* and put an asterisk (*) in order to make a comment. The comment is on the publisher of the science journal, which is the Oxford University Press on the behalf of the Society for Molecular Biology and Evolution.
	* For the number of pages, I bolded the subtitle "Number of Pages:", and then typed in a space and a the number 12 (as accordance to the PDF version of the paper).
	* For the 3 outcomes of the paper, I bolded the subtitle, "Three Outcomes of the Paper: ". Then in new lines, I listed (numerically) the three most significant results from the paper. I also provide detail explanation(s) in a form of an unordered list under each result. This is to provide clarification on the subject matter at hand.
	* For the link to the paper online, I bolded the subtitle "Linke to the Paper Online: ", and then copy and paste the link to the Markdown file.
4. Once all the right information is put in and orderly structured, I pressed the "present new file" button to finalized the creation of the Markdown file.
5. Lastly, I checked to make sure the file is ready to be send back to the "igorsteinmacher/INF502-Fall2020", and I pressed the "create pull request" to comence the action.
```
