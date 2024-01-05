# What is Git? 

With your project growing bigger and bigger, it is very hard to manage the versions, especially when most projects have hundreds and even thousands of files. 

Linus created Git for managing his Linux system code. Git is distributed version controll system, which means everyone has a complete copy of the entire history project. So any coder can just start from picking a piece of code and then work on it, then giving back to the project after finished.

Also the idea of forking and merging is very simple to do in git but not in others. 

# Git model in a few sentences

1. It will hash all the files and, the hash result is always unique to the orignal file.(files)

2. The idea of tree is snapshotting the current version of the repo. (trees)
     
3. It also tracks the who is the author, why they are making changes of files, which tree of files changed, what the changes are, and when it was changed.(commits)

4. The folder is hidden so the repo is super clean even the history and long. (.git)

5. Git is capable for handling conflicts between the authors.

# Git basic 

Whenever you type commands, git will change the content inside the .git dir. 

## Git init
  You barely would need this command because 90% of the time other coders already started the repo. 

```md

cd dirname

git init


# start the git repo with the initial branch called main
git init --inital-branch=main


```

### The basic way to start a repo

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/650ded7a-1964-4cec-8a17-f8965e11ff83)


## git status

```md
# This is checking the status of my repo. 
git status

```
![image](https://github.com/zkrguan/my_git_notes/assets/97544709/f9538d3f-cf8e-4395-bc44-0ce65e0e7986)


```
# If I create a file and use git status to check again.
touch file1

git status

```

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/baee29c3-170f-4d79-9a69-049e2898527f)


### What is untrack file then?

You added the file but git does not have a snap shot of it, which means git is not currently tracking the file.

So how to make the git track this new file?

## git add

```md
# git add fileName will move the file into the staging area. 

git add fileName

```
![image](https://github.com/zkrguan/my_git_notes/assets/97544709/78800d2a-0ea0-4973-b82e-ca37be762fb2)

### But first of all, what is a staging area?

It is not visiable inside the repo. But it is acting like a cache. So cache of what? *** cache of the current state of the file *** the staging area tells the git what the next file snapshot will look like. So, staging area is like ready to make snapshot area.  

Think about the hell's kitench. Second line cooks prepare the ingredients for the first line cook. And first line has a area for the processed ingredients from the second line. That area is a perfect example of the staging area.

### Why you don't want to use git add * or git add . ?

Because you will add too much into the staging area. 

## git commit

This is making the snapshot official and recorded by git.

```md

# the most common way to make commit
git commit -m "the summary"


```

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/a6ef9167-ad95-418b-8801-1f64ed8255f2)

## git log

This is the way to check where you at regarding commits. 

```md

git log 

```
As you notice commit name is hashed.

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/6ed4e900-9a43-4dba-b98c-1df30c6faa64)

actually git stores all the histories inside the git/objects/ 

### Why would you bother to have a staging area? It is like a waste of the step...

People ask this kind of questions must have not experienced working in a real life project. 

A. Sometimes, one large change could cost multiple commits to finish because you don't want to suddenly have 1000 lines changed and then you need to hot fix. Modulize your work isn't just saying. 

B. It is making easy for other coders to review the changes inside the git log. 

C. Staging also can help people resolve conflicts when merging a branch.


## git diff

```
# This is a command used combo with git status

git status

git diff

# example use case I modified and then want to check what I have changed

```

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/ea832053-eb0d-451b-8c89-f258d35c2e74)

\+ meaning added
  
\- meaning removed
  
+1 -1 meaning I added one removed one ,2 meaning there are totally 2 lines changed.


## git rm fileName

```
# This will do two things.

# 1. remove the file from the staging area.
 
# 2. remove the file from the working repo on the computer. 

git rm fileName

```
A perfect example of walking through git rm fileName

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/5186238e-55d6-414d-ace4-881e55eab404)

But did you remove the file totally? No because inside .git, there is a previous version of the working repo. So there is a way to recover back from the file. Will be covered in the next section. 

## git restore fileName

```
# Be aware that this is NOT restoring the file from the .git
# This is restoring from the staging area.

git restore fileName

```

Some experiments

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/b86d44e3-59da-423c-8a23-69518aa877d7)

## git clone repoName

```
# This will literally clone everything from the other git repo even the histories.

git clone gitRepoName newRepoName

# most commonly you would use this command combined with the github url for example

git clone url localRepoName

```

example of proving copying everything from the local repo

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/c250f870-41d7-4757-b4fe-7871b74bec99)

example of copying one from the github with github URL

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/a69056bf-5ad0-43e0-90f0-4a544e3cded7)


*** github forking is just like git cloning. ***

Why forking?

You don't have the write access to the github repo. Forking makes you have your own copy of the code from the upstream repo. Changes will be saved into your forked version. 

If you are the contributor, you could even create PR to make contributions to the upstream repo. 

________________________________________________ End of the basic commands _____________________________________________

# Branch and Tag

Back to the logic of git, git uses the hash values to name each commit like the pic below, and it is very good because the hashed name will never be same unless the files are identical on the byte level.

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/b509a265-912a-4072-a391-43d8cc178a32)

It is good for the computer, but to the developers, how can you just let your coworker know you are on commit abc79c0695af38931da06ade20b85c2224fc682a? It is such a headache to talk to each others. 

As a matter of fact, git provides two tools for handling communication between developers rather than using the hashed values.

## git tag

```

# starting from cloning my school's open source project.

git clone https://github.com/Seneca-CDOT/telescope.git telescope


# check tags

git tag

```

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/1bda2030-6dc5-4253-b588-b183f913af75)

These number meaning?

Each tag means a release. So my school's project has 57 releases. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/46f04a42-475b-4699-9bbf-e773f593889b)

If you click into, you could see more detail information about each releases. Each release means a version of softwares. 

Instead of hashed commits, you only need to document the release tag names and the description of each release, which makes this easier. So tag is just a aliase to a commit. 

How to make a release then? 

```

# This is only one of the many ways to make the tags. 

git tag -a version code -m "Your release message goes here"

```

Let's say the developers are working on the newer version, but the users are having issues with the older version. The developers are assigned to work on the old versions to resolve the bug. Introduce time machine git checkout.

### git checkout ( the time machine ) 

```
# use git checkout to rewind the time to version 0.6.0

git checkout 0.6.0

```

The screenshot tells 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/e542f83f-4623-41a1-8cd5-f6ad37d3b7c6)

Yep, I made my HEAD sit on the first release commit made by my prof 3 years ago.

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/e488c668-a545-402f-9352-3ad7fad171d6)

This will do the same thing as well, but with the hashed value from the git commit.

```
# use git checkout to rewind the time to version 0.6.0's commit 

git checkout 8e984f9545922e7c033f4377ff5729d1bf0d041c

# Or you could use first 8 letters will do the same too

git checkout 8e984f95

# to quickly go to the most recent commit

git checkout master

```

Although tag is good, branch is more often used in the production environment. 

## git branch

Branches are totally local before you upload the branches to the Github. 

```

# This will list all the avaliable branches

git branch

```

You see the HEAD is pointing at the master branch. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/0b165035-3419-475d-a388-5046c91cf4fb)

```

# how you create a new branch

git branch branchNameGoesHere

```

Like this is how I created a new branch in my local repo. (reminds me the old time working with friends.)

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/44f13a58-7c7e-411b-bb88-4a4113a6437b)


```

# This is how move from one branch to another

git checkout branchName

```

Notice the head to pointed at newly created branch.

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/c31d5a0c-e20d-487b-81a7-1cdaef0933b3)

```
# Normally you would use this to do avoid type two commands 
# creating new branch and swithcing to that branch at the same time.
git checkout -b branchName

```


Be aware that all the commits will be added to the branch while you are on that branch. So the branches makes the developers an isolated space for them to work on without effecting others. After you switch to another branches, you could not see the commits because those commits are sitting on the other branch. 

IF YOU CHANGE FILES AND DID NOT COMMIT, AND THEN YOU WANT TO SWITCH BRANCH. GIT WILL BLOCK YOU FROM DOING THAT. 

Also, when you make a new branch, the previous commits will be brought over depends on which was your current branch.

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/a3d2b20b-1f96-41fb-ba0c-15a2ced8dfe8)

If you don't want the branch because it is total failure. 

```
git checkout master

# If you DO NOT have commits did not bring to the master
git branch -d branchName

# If you have commits that don't need anymore for the master
git branch -D branchName

```

Demo:

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/204b7513-b155-4053-a909-a39bcce6504c)

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/5f81f4d6-429a-4582-8f24-ec64c404e4a9)



