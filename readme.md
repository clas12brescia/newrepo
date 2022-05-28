## Test of mergin repos.

Existing repositories:

(1) testarea: https://github.com/clas12brescia/testarea

(2) test2: https://github.com/clas12brescia/test2

Each repo has its own commit history. In addition, testarea has several branches. https://github.com/clas12brescia/testarea/branches

TEST: can we merge them as subdir of a new project preserving each repo history?

ANSWER: yes, but 1 branch per repo


## Log

making new repo: 

```mkdir newrepo 
cd newrepo
git commit --allow-empty -m "Initial dummy commit"
```


### ADDING TESTAREA

Add a remote for and fetch the testarea repo
(the '--fetch' (or '-f') option will make git immediately fetch commits to the local repo after adding the remote)
```
git remote add --fetch testarea https://github.com/clas12brescia/testarea
```
Merge the files from testarea/main into new/master
```
git merge testarea/main --allow-unrelated-histories
```
Move the testarea repo files and folders into a subdirectory so they don't collide with the other repo coming later
```
mkdir testarea
ls -I testarea | xargs -i git mv {} testarea
git commit -m "Move testarea files into testarea subdir"
```

### ADDING TEST2

```
git remote add --fetch test2 https://github.com/clas12brescia/test2
git merge test2/main --allow-unrelated-histories
mkdir test2
ls -I testarea -I test2 | xargs -i git mv {} test2
git commit -m "Move test2 files into test2 subdir"
```










