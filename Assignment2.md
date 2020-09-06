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

7. Write a command (or sequence) to commit your changes

```

```

8. Change back to the `master` branch and change B.py adding the following source code
(commit your change to `master`):

```

```

9. Write a command sequence to merge the `math` branch into `master` and describe what
happened

```

```

10. Write a set of commands to abort the merge

```

```

11. Now repeat item 9, but proceed with the manual merge (Editing B.py). All implemented
functions are needed. Explain your procedure

```

```

12. Write a command (or set of commands) to proceed with the merge and make `master` branch
up-to-date

```

```

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

```
