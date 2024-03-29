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

```md
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

```md
# This will do two things.

# 1. remove the file from the staging area.
 
# 2. remove the file from the working repo on the computer. 

git rm fileName

```
A perfect example of walking through git rm fileName

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/5186238e-55d6-414d-ace4-881e55eab404)

But did you remove the file totally? No because inside .git, there is a previous version of the working repo. So there is a way to recover back from the file. Will be covered in the next section. 

## git restore fileName

```md
# Be aware that this is NOT restoring the file from the .git
# This is restoring from the staging area.

git restore fileName

```

Some experiments

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/b86d44e3-59da-423c-8a23-69518aa877d7)

## git clone repoName

```md
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

```md

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

```md

# This is only one of the many ways to make the tags. 

git tag -a version code -m "Your release message goes here"

```

Let's say the developers are working on the newer version, but the users are having issues with the older version. The developers are assigned to work on the old versions to resolve the bug. Introduce time machine git checkout.

### git checkout ( the time machine ) 

```md
# use git checkout to rewind the time to version 0.6.0

git checkout 0.6.0

```

The screenshot tells 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/e542f83f-4623-41a1-8cd5-f6ad37d3b7c6)

Yep, I made my HEAD sit on the first release commit made by my prof 3 years ago.

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/e488c668-a545-402f-9352-3ad7fad171d6)

This will do the same thing as well, but with the hashed value from the git commit.

```md
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

```md

# This will list all the avaliable branches

git branch

```

You see the HEAD is pointing at the master branch. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/0b165035-3419-475d-a388-5046c91cf4fb)

```md

# how you create a new branch

git branch branchNameGoesHere

```

Like this is how I created a new branch in my local repo. (reminds me the old time working with friends.)

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/44f13a58-7c7e-411b-bb88-4a4113a6437b)


```md

# This is how move from one branch to another

git checkout branchName

```

Notice the head to pointed at newly created branch.

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/c31d5a0c-e20d-487b-81a7-1cdaef0933b3)

```md
# Normally you would use this to do avoid type two commands 
# creating new branch and swithcing to that branch at the same time.

git checkout -b branchName

```


Be aware that all the commits will be added to the branch while you are on that branch. So the branches makes the developers an isolated space for them to work on without effecting others. After you switch to another branches, you could not see the commits because those commits are sitting on the other branch. 

IF YOU CHANGE FILES AND DID NOT COMMIT, AND THEN YOU WANT TO SWITCH BRANCH. GIT WILL BLOCK YOU FROM DOING THAT. 

Also, when you make a new branch, the previous commits will be brought over depends on which was your current branch.

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/a3d2b20b-1f96-41fb-ba0c-15a2ced8dfe8)

If you don't want the branch because it is total failure. 

```md
git checkout master

# If you DO NOT have commits did not bring to the master
git branch -d branchName

# If you have commits that don't need anymore for the master
git branch -D branchName

```

Demo:

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/204b7513-b155-4053-a909-a39bcce6504c)

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/5f81f4d6-429a-4582-8f24-ec64c404e4a9)

________________________ End Of the branch and tag ________________________


# merge, diff, and more

## git diff

```md
# git diff can be used to check the difference in the staging area and the commited works

git diff

# or you could use git diff commit1 commit2 in order to compare both commit's difference

git diff commit1 and commit2

```

this command will show what is the difference between two commits. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/a064d31d-2f68-4358-9f17-0b333380abb1)


## git merge

When we want to bring the commits from ONE branch to ANTOHER branch, there are multiple ways. The following screen shot shows how did I create a new branch and then make commit on the new branch. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/859f8617-4ff3-4530-b89a-124a3820b905)

You can see the testingBranch is what people called 1 commit ahead of the main

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/ba24f9d0-4766-48de-a357-d6e785dfcf29)

If you want to bring the commit from the testingBranch to the main branch, we could use git merge

### First approach ( ideal case )
```md

# Step1 move to the branch you would like to merge the commits TO:

git checkout master

# Step2 merge

git merge branchName

```
Demo:

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/90a22b89-d9fc-49eb-aadb-effc333be051)

Output:

Notice your main and the testingBranch are on the same commit now.

This is ideal case of the merge because of the fast forward merge.

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/18f3cf29-3d06-4eca-bbbb-a13bc892b604)


```

# This will actually make the master branch go back to the commit you provided
# Understand this as a reset

git checkout -B master commitName

# You could actually specify how to merge for example this command below

git merge --ff-only branchName

```

You recover the branch by using git checkout -B 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/6e3dc121-3236-4b20-a8b4-3cb66dc30339)

However, not everytime, when you are trying to merge your branch, the master (main) has no changes. 

Because think about it, your team has more than 400 coders, the main is constantly updating by every coder. 

So the second approach is here. 

### second approach ( real in the production )

#### issue identify

Like I mentioned on the above, the master is heading to a direction that testingBranch is not going. 

Why you cannot see the where the master is?

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/81d3a606-7708-48e0-9859-53dc2fa213e3)

As a result, I still use git merge --ff-only testingBranch

It shows an error:

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/0db26ab2-e19a-4eb8-b1b6-a8550cc4a72f)

Because file2's first line has two versions now. Git is confused which version should it use. So the auto merge won't work because of the conflict.

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/6fff3106-adb1-4b34-a89b-6faf1a439651)

If you type down git status from the main branch, here is how it looks. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/7af80269-7f65-44e5-94ae-9c99cde89b2f)

#### Already, so how to finish the merge?

open the file with conflict with your favorite editor. 

git already marked the conflicted area for ya. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/149bb019-23c3-4a03-aed8-b2d18bb2098c)

The equal signs divide the two versions. And the version has been marked for you. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/65a25b82-ee64-4021-b6b9-abaf9f90c72e)

So you just need to clear the special symbols + the version you want to keep. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/b27468f5-7b14-4b08-a3b5-e2be2302e635)

After modify, you still have to add and commit. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/d70e2815-b773-4913-9d43-55bfe53c7a8e)

Yep, so this is how you manually merge them. And you notice the lastest commit is just like a bridge merged two branches together. 

This is called ** recursive merge **. 

### Bonus abort merge:

Sometimes the conflict is too big. You don't know what to do, and you don't want to leave the mess behind. 

```md

git merge --abort

```

____________ end of the git merge ____________


# remote git ( mainly about github and the git commands related )

## Up stream repo and github fork

Think about the source of St.lawrence is Lake Ontario. Lake Ontario is the up stream repo of the St.Lawrence. 

Most github Projects you won't have the access to commit or other things. That's why the github allows you to FORK. 

upstream repo

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/88bf5b31-d29a-4682-a1f8-293703ba740c)

forked version

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/1a01d287-19fc-4159-a496-9f3c7c43fac3)

Then, on your forked version, you could git clone to your own computer and then make commits to it. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/bdcf198b-11b2-41aa-8495-cb4d6e8ed2df)

Finally, after finishing editing, you could just update the upstream repo by using PR or other tools. 

( I'd better not mess around with them )

## git remote
```md
#This is to where the current repo orginated from 

git remote -v

```
Example here shows the forked version and the original version 

the git remote command shows where the code comes from

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/01997f03-4ea0-437d-9a0d-f733f2974ada)

```md

#You could also add a remote instead of forking it
#Example here I used this to add the add a remote in the forked version

git remote add upstream https://github.com/Seneca-CDOT/telescope.git

```

Now it is added, but how does this work?

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/ad98a503-cfae-416d-8537-ad28c668232d)

## git fetch origin

```md
# this won't have anything happen because there is no commits has been made to the forked repo. 

git fetch origin

# But what if I fetch from the upstream which I just set up from the command above.

git fetch upstream

```

A whole buntch of tags and branches got brought over to here from the upstream:

*FETCH* WILL ONLY DOWN LOAD BUT NOT UPDATE CHANGES

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/78774812-9d18-4f32-8fc9-dc0a9f8cdcd7)

## remote branches

first two commands are quite easy to understand. But what about the command with -a

```md

# This will print out all the remote branches

git branch -a


```

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/ba4102fc-8305-419b-b8f3-75b6c4e5b411)

what if I want to switch onto those remote branches?

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/d9ea947c-ce9c-4925-8eb3-aed73756e218)

Prove I was not lying:

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/2685ee07-ae85-4114-8e9e-6239854b8f72)

You see the how to git add remote git fetch download and bring the branches and tags from the upstream repo. 

Sometime you could just use git merge upstream master to bring the new commmits back to the forked version

```md
# This is very nice when the merge is fast forward merge

git merge upstream/master

```

## git pull

When you do a pull, it will fetch and merge the upstream master to the local master. This could cause files changes, and sometimes the changes can be unwanted. 

It is just like a combination of the two commands we made from the above.

```md
# although you learned this long time ago, it is still very dangerous to use because it could bring the unwanted changes. 

git pull upstream/master

```
**Never run this on a topic branch** Because this will change files. Only run this on your main. 

But what is the use of these remote, fetch, merge of the above mentioned commands. You could actively work with the developers in your team when you have a problem. How? 

## Work flow demo

### Basic pattern. 
```md
     # 1.forked the project to your own github

     # 2. Add the upstream remote

          git remote -add upstream URL

     # 3. This will download all the remote branches and tags and more to your forked repo.

          git fetch upstream

     # 4. Then make sure you are on the main of the forked version, then merge with the upstream master(or main)

          git merge upstream/master


     # As a matter of fact, in the product env, you could do step 3 and 4 constantly every morning maybe to keep updated with your upstream repo.
     # git pull upstream master could be used more often because 1 < 2. But sometimes, you do care what you are merging. Use 2 step approach. 
```

### Handling PR branches from the remote (Senior level?)

First of all, PR is a request to merge from a branch to another branch. That upcoming branch can be from the same repo or forked repo of the other team members.

So this git pattern is made for Senior to check your work. 


```md

# Senior POV there is a new PR created for the working repo.

     Go to github PR, and check which guy's which branch was trying to merge with the main. (normally junior could only merge to the dev, and senior would do the PR from the dev to the main because there are CD pipelines in the main)

# Then the senior will go to the junior's forked repo and copy the https URL. Then add the remote to senior's remote

     git remote -v

     git remote add juniorName juniorURL

     git remote -v
     
# Then copy the junior's repo's branches from the remote.

     git fetch junior'sName

# Create a branch on Senior's branch based on Junior's Branch
# This is creating a branch to track junior's branch from a senior's repo's branch

    git checkout -b meaningfulName juniorName/juniorPrBranchName
     
# Then you can test the junior's branch from your local machine in your tracker branch.
# After confirming everything is good, you could just merge the PR.

```

*don't ever commit anything on the main (unless it is an emergency fix)*

## git push 

This will send all the commits to the remote you sepcified 

```md

# assume you make a hot fix and commited on your local 

# this is pushing to the github repo so the CICD pipe line will deploy the rest into your container. 

git push origin master

__________________________________

# or even you created a new branch

git checkout -b newBranch

# you commit your changes

# you push everything up to the forked repo.

git push origin master

# Now you would see a branch created on the github of your forked repo.

```
### always remember pull first then push 

Think if one of you pushed the changes to the main. 

The other forgot to pull the change and made commits and now he is ready to push. 

What will happen?

git will reject your change request. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/14836bed-0501-4a4d-9ef1-cae76bcfde05)

Bruh what now? Never never do the command below, this will destory everything. 
Git will delete the commit made by the other person and upload the commit. (your commit replaced the other person's commit which is wild!!!) 

*yell at gpt4 if it is giving this anwser*

~git push origin issue-555 --force~

What is the proper way then?

### if you forgot to pull and made commits

```md
# It is not too late to pull.
# If there is conflict, resolve them with your team mate.
# This will create a recursive merge ( you will see a PR made and merge automatically)

git pull remoteName branchName

# now it should be good to push.
git push remoteName branchName

```

_________ end of the git remote section _________


# git rebase 

## git commit --amend

### replace the previous commit

Before rebase, here is how to fix a commit has been made by you. 

```md

git commit --amend

```
This will show the most recent commit you made on this branch

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/5dd60fc5-838a-44b6-9c9e-59f42bbc0741)

You could actually make changes for the commit message you made by using the editor. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/d486af84-7faf-43be-a5f1-e5ab67ebe9fe)

Save and check with git log, the commit message was changed. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/8947f1c5-2c8f-4af0-8fa5-a82676669fa3)


What we have done? We just changed the history of the git. The example above is easy, but look at here. 

git commit --amend is actually making a new commit to replace the most recent commit. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/0939e16c-608a-4810-ad1f-2b3efa7ec871)

If I want to push the changes now, it won't work. ( my github auth had problems used prof's vid snip)

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/43773e5d-f86c-4f98-9acd-371443298bf5)

Because your GitHub repo is sitting on the old commit (c1)

Your local is sitting on the new commit made by the commit --amend (c2)

What you should do now? 

```md

git push origin master --force

```
WTF you just told me don't do this now you told me this is the solution?

Here is the reason. Remember this will **eliminate** the commit on the GITHUB and **push the local commit** to the branch. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/f4206ff8-7635-4873-8848-60d03e8f1527)

At the end, only the second commit exists. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/477a0269-3d3b-432f-af80-f07ef2c1ba95)

### add the current commit to the previous commit. 

After made a commit, you forget to add something in the readme, and you don't want to create a new commit for fixing it. 

Here is how we do this.

```

# edit

# git add the file to the staging area

git add fileName

# make commit but no need to change the commit message

git commit --amend --no-edit

```

You just slide the changes into the previous commit, which saves some hassels. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/6d089d78-a9c7-4b4d-a25f-487808aa73ba)

add -> amend --no-edit

none of these above are as powerful as this one here. 

## git rebase

I had issues while I am developing on the feature, at the same time, @kev fixed some of his login logics. As a result, my topic branch is not updated with the master branch because Kev merged his branch with PR. 

At that moment, I started PR **FROM** main **to** my branch. But it could create tons of conflicts if I was working on log in logics too. 

Anywaybetter ways to resolve this? 

git rebase is working like a time machine. You travel back to where you forked. 

### step by step using git rebase to clean the git histories

```md

# make sure you are on the topic branch then
# this command will calculate the difference between your branch and the master branch
git rebase branchName  

```

First I made changes (readme) on the MASTER:

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/feddcbed-d02d-461b-8ccd-2f14b9007d44)

Then of course changes are remained on the MASTER. I went to the topic branch, and indeed changes are not showing.

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/384bf981-3437-4f32-9bae-822da3525f2d)

Then I ran the git rebase master

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/b1b2f657-6880-49e3-9ee3-3f3cd072750e)

Boom the changes are here now.

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/a13044ee-fc77-430d-8956-2bf19374548c)

You could understand that git rebase branchName will make the current branch carry all the commits from the branchName. So it is like the previously the topic branch is based on one commit. Now, after git rebase, the topic branch is based on the most current commit from the branchName. (Like changing a new base for a building.)

Think about a old PR you forgot to merge. When you try to merge it, you realize this is too old and it is not good idea to merge it. It will be the perfect one to use git rebase master to update it with the master's most recent commit. 

If there are too many conflicts, you could just follow the commands from the terminal to either abort, skip, or more. 

```md

# If the situation is more complicated, use **interactive rebase**

git rebase master -i

```

You can manually choose what to do with each commit. 

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/0710808a-c31c-4a73-9c5e-5b1a91ee75e0)

melding meaning combining second one into the first one. So made it to a single commit. 

You basically just put the words front of each commit, so the git will do the instructions you specified. 

Save and exit, git will ask you to make a commit message. 


