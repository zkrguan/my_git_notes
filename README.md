# my_git_notes

Yet another note repo for git and github. This will be the cheat sheet or receipt book.

## What is Git? 

With your project growing bigger and bigger, it is very hard to manage the versions, especially when most projects have hundreds and even thousands of files. 

Linus created Git for managing his Linux system code. Git is distributed version controll system, which means everyone has a complete copy of the entire history project. So any coder can just start from picking a piece of code and then work on it, then giving back to the project after finished.

Also the idea of forking and merging is very simple to do in git but not in others. 

## Git model in a few sentences

1. It will hash all the files and, the hash result is always unique to the orignal file.(files)

2. The idea of tree is snapshotting the current version of the repo. (trees)
     
3. It also tracks the who is the author, why they are making changes of files, which tree of files changed, what the changes are, and when it was changed.(commits)

4. The folder is hidden so the repo is super clean even the history and long. (.git)

5. Git is capable for handling conflicts between the authors.

## Git basic 

Whenever you type commands, git will change the content inside the .git dir. 

1. Git init
  You barely would need this command because 90% of the time other coders already started the repo. 

```md

cd dirname

git init


# start the git repo with the initial branch called main
git init --inital-branch=main


```

// The basic way to start a repo

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/650ded7a-1964-4cec-8a17-f8965e11ff83)


2. git status

```md
// this is checking the status of my repo. 
git status

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/f9538d3f-cf8e-4395-bc44-0ce65e0e7986)


// if I create a file here here and type the git status again

touch file1

git status

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/baee29c3-170f-4d79-9a69-049e2898527f)


```

What is untrack file then?

You added the file but git does not have a snap shot of it, which means git is not currently tracking the file.

So how to make the git track this new file?

3.  git add

```md

git add fileName

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/78800d2a-0ea0-4973-b82e-ca37be762fb2)

```
git add fileName will move the file into the staging area. 

But first of all, what is a staging area?

It is not visiable inside the repo. But it is acting like a cache. So cache of what? *** cache of the current state of the file *** the staging area tells the git what the next file snapshot will look like. So, staging area is like ready to make snapshot area.  

Think about the hell's kitench. Second line cooks prepare the ingredients for the first line cook. And first line has a area for the processed ingredients from the second line. That area is a perfect example of the staging area.

4. git commit

This is making the snapshot official and recorded by git.

```md

// the most common way to make commit
git commit -m "the summary"

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/a6ef9167-ad95-418b-8801-1f64ed8255f2)

```

5. git log

This is the way to check where you at regarding commits. 

```md

git log 

// As you notice commit name is hashed.

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/6ed4e900-9a43-4dba-b98c-1df30c6faa64)

```
actually git stores all the histories inside the git/objects/ 



### Why would you bother to have a staging area? It is like a waste of the step...

People ask this kind of questions must have not experienced working in a real life project. 

A. Sometimes, one large change could cost multiple commits to finish because you don't want to suddenly have 1000 lines changed and then you need to hot fix. Modulize your work isn't just saying. 

B. It is making easy for other coders to review the changes inside the git log. 

C. Staging also can help people resolve conflicts when merging a branch.


6. git diff

```
// This is a command used combo with git status

git status

git diff

// example use case I modified and then want to check what I have changed

![image](https://github.com/zkrguan/my_git_notes/assets/97544709/ea832053-eb0d-451b-8c89-f258d35c2e74)

```

\+ meaning added
  
\- meaning removed
  
+1 -1 meaning I added one removed one ,2 meaning there are totally 2 lines changed.



