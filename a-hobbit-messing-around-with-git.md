# A Hobbit Messing Around with Git

Hi handsome, my name is Paulo Leonardo Benatto (a.k.a hobbit, dwarf or whatever you want
=) and I would like to share my little experience working with git in different teams.
If you are reading this document maybe you want to share your experience as well.

As I said before, this document is my experience working with git when I used to live and
work in the Shire and Bree (north west of Middle-earth). You shouldn't take this post as
a git reference, there are a lot of papers on the Internet explaining different git
workflows and you should read them all.

If you do not agree with what I wrote here please send me comments or open a new issue in
this repository. Just to be clear `you suck hobbit` is not a nice comment, I'm a hobbit
with feelings.

## Nomenclature

Nomenclatures, standards and codestyle are usually subject for flame wars and this is not
what I want here. I'm an open-minded guy (I live in Brighton =) and I accept different
opinions. However I do agree that a team need some kind of standard to name branches,
to make commits messages and a git workflow.

I do not have the monopoly on truth, when I work alone I do not use branches and my commit
messages suck. I know I shouldn't do that and I promise that I will try to police myself.

Ok hobbit, tell me a good way to solve nomenclatural problems? All companies I have worked
in UK use Jira tool to manage projects and issues. It is possible to integrate Jira and Git.
A good advantage using this solution is that your manager or agile coach can easily follow
what the developer is working on and see the status of the tasks.

Ok, pretend we have a project on jira called `frodo` and every ticket (bug or feature) inside
the project has the name `frodo-XXX`. In the moment the developer has to fix a bug or create
a feature he can create a branch with the ticket name and all activities inside of the branch
can be seen in the jira ticket. You also can see the description of the problem in the jira
ticket.

I will be honest with you, as a developer I do not like to work with Jira :), I prefer to be
coding in a black terminal all day long. However I make an effort because I know how important
a dashboard is for team leaders, managers, agile coaches and communication in general.

If we do not use Jira to name branches, is there another option? Yes, look this paragraph from
the document Understanding the Github Flow.

```
Because of this, it's extremely important that your new branch is created off of master
when working on a feature or a fix. Your branch name should be descriptive (e.g.,
refactor-authentication, user-content-cache-key, make-retina-avatars), so that others
can see what is being worked on.
```

If I could choose I would vote for using Jira, but I agree that is a team decision.

## The beginning

Ok hobbit, stop the jibber jabber and start showing something useful.

We always start contributing to a project cloning or forking it, right? Here I will
not talk about the fork approach only creating a branch in the repository because I
think this is easier and more common.

```
git clone git@github.com:BrandwatchLtd/paulo-hobbit.git
```

If you have already the project cloned in your machine just remember to update the project
before creating a new branch. To update your repository you can use `git pull` or `git fetch` and
`git merge` they are equivalent.

```
# cd paulo-hobbit
# git pull
```

## Create a branch

Ok, let's create a new local branch to add new feature or bug fix. Like I said before the
name of the branch depends on the name of the convention adopted by the team. This command
will create a new branch and change to the new branch.

```
# git checkout -b paulo-is-hobbit
```

If you are using a shell that shows  you the name of the branch you should see something similar to that.

```
➜  paulo-hobbit git:(paulo-is-hobbit)
```

## Push your Changes

Now we have a branch and we can start changing our code, so make all changes necessary
in the project to fix your bug or add a new feature. Let's try to keep in mind the
philosophy do one thing and do it well.

![](/imgs/emacs.jpg)

```
# git add file1.rb file2.pp file.txt
```

A good commit message is important and helps developers track issues if they go through
git log command. I'm terrible writing commit messages and I have a lot to improve.

```
# git commit -m "message"
```

Have a look in the paper: [Introduction: Why good commit messages matter](http://chris.beams.io/posts/git-commit/)

In this moment the branch `paulo-is-hobbit` is local, only you can access it, but we want
to share our code with the whole team, so let's send our branch to the remote.

```
# git push origin paulo-is-hobbit
```

It Is possible to set the upstream with the option `-u`. If you go to the github repository you
should be able to see your branch and create a `Pull Request`.

![](/imgs/pr.png)

## Create a Pull Request (PR)

```
Pull requests let you tell others about changes you've pushed to a GitHub repository.
Once a pull request is sent, interested parties can review the set of changes, discuss
potential modifications, and even push follow-up commits if necessary.”
(Pull Request tutorial by yangsu)
```

Share the PR link with your friends using slack, email, whatsapp, telegram, ICQ, IRC
and Usenet. Make sure they receive your PR because Code Review (CR) is really important
for the success of the project and a lot of developers don’t like to do it.

If your colleagues wrote comments in your PR:

```
while (msg != 'LGTM') {
	be angry in silence;
	make the changes the TEAM asked you;
	commit and push your code again;
}
```

**IMPORTANT**: If you are doing Code Review you should test the new feature and try to
run the code as well. If you are approving the PR means that it works for you.

**LGTM**: Looks Good To Me.

## Squash your Commits

After the team approved your PR, your branch probably has some commits and IMHO is easier
to read if we have one commit per feature or bug fix. We can squash commit messages and
integrate your changes with the default branch using interactive rebase.

Guys, I will not start another war because you prefer merge, rebase or don’t like to squash.
Please suffer in silence and stop reading this post. hehehe I’m an evil hobbit. I'm pretty
sure we can achieve a consensus as a team.

Let's pretend the name of your default branch is master, but it can be 'production', 'develop' or whatever.

```
# git rebase -i master
```

When I type the `git rebase` command opened to me an editor (Vim for me). In this moment
I can squash and change my commit message.

```
pick 5b35582 it is a test                                                                                           
pick 03d558c test                                                               
pick 5213cdd Update section squash                                              
pick e0b6202 Fix typo on conclusion section                                     
pick 77b1bdb Remove section drwarf                                              
pick 0884b83 Add section solving conflicts                                      
                                                                                
# Rebase cc21c7b..0884b83 onto cc21c7b (6 command(s))                           
#                                                                               
# Commands:                                                                     
# p, pick = use commit                                                          
# r, reword = use commit, but edit the commit message                           
# e, edit = use commit, but stop for amending                                   
# s, squash = use commit, but meld into previous commit                         
# f, fixup = like "squash", but discard this commit's log message               
# x, exec = run command (the rest of the line) using shell                      
# d, drop = remove commit                                                       
#                                                                               
# These lines can be re-ordered; they are executed from top to bottom.          
#                                                                               
# If you remove a line here THAT COMMIT WILL BE LOST.                           
#                                                                               
# However, if you remove everything, the rebase will be aborted.                
#                                                                               
# Note that empty commits are commented out  
```

To squash my commits I will change the first commit message and put something
useful about my feature or bug fix. I have changed:

 * First line change `pick` to `reword` because I want to change the commit message.
 * The other lines I change `pick` to `f` (fixup) like "squash", but discard this commit's log message.

```
r 5b35582 it is a test                                                          
f 03d558c test                                                                  
f 5213cdd Update section squash                                                 
f e0b6202 Fix typo on conclusion section                                        
f 77b1bdb Remove section drwarf                                                 
f 0884b83 Add section solving conflicts    
```

Save the file and let's change the commit message. The commit message is: it is a test and
change for something more useful like: *Create a document about git workflow*. Save the file =).

```
Create a document about git workflow                                                                                                    
                                                                                
# Please enter the commit message for your changes. Lines starting              
# with '#' will be ignored, and an empty message aborts the commit.             
#                                                                               
# Date:      Thu Aug 4 09:27:39 2016 +0100                                      
#                                                                               
# interactive rebase in progress; onto cc21c7b                                  
# Last command done (1 command done):                                           
#    r 5b35582 it is a test                                                     
# Next commands to do (5 remaining commands):                                   
#    f 03d558c test                                                             
#    f 5213cdd Update section squash                                            
# You are currently editing a commit while rebasing branch 'paulo-is-hobbit' on 'cc21c7b'.
#                                                                               
# Changes to be committed:                                                      
#>------modified:   README.md   
```

Go to the github project and have a look in your pull request.

![](/imgs/onecommit.png)

## Resolving Conflicts

Resolving conflicts is part of our lives and is not that bad, we just need be
patient. Removing your branch and starting from scratch **IS NOT A GOOD SOLUTION**, 
keep calm and fix the conflict.

 * I did changes in my branch `paulo-is-hobbit`
 * I also did changes in my `master` in the same file.

In this moment the branch `paulo-is-hobbit` has conflicts that must be resolved.

![](/imgs/conflict.png)

Ok, let's start the rebase process again, but now we have to fix the conflict.

```
# git rebase -i master
```

It will open the editor again and you should do the same squash process.

```
r 17b274d Create a document about git workflow                                  
f 934751b Improve conclusion   
```

When you save the file you will see this beautiful message.

```
error: could not apply 17b274d... Create a document about git workflow

When you have resolved this problem, run "git rebase --continue".
If you prefer to skip this patch, run "git rebase --skip" instead.
To check out the original branch and stop rebasing, run "git rebase --abort".
Could not apply 17b274dfd187305ce65aca98c13a54243117186c... Create a document about git workflow
```

First thing let's see the unmerged files:

```
# git status
```

```
interactive rebase in progress; onto 7b8a5f1
Last command done (1 command done):
   r 17b274d Create a document about git workflow
Next command to do (1 remaining command):
   f 934751b Improve conclusion
  (use "git rebase --edit-todo" to view and edit)
You are currently rebasing branch 'paulo-is-hobbit' on '7b8a5f1'.
  (fix conflicts and then run "git rebase --continue")
  (use "git rebase --skip" to skip this patch)
  (use "git rebase --abort" to check out the original branch)

Unmerged paths:
  (use "git reset HEAD <file>..." to unstage)
  (use "git add <file>..." to mark resolution)

	both modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

Look: `both modified:   README.md` let's open the file and fix the
conflict.

```
# vim README.md
``` 

Save the file.

```
# git add README.md
# git rebase --continue
```

```
[detached HEAD b5c9ba1] Create a document about git workflow
 1 file changed, 264 insertions(+), 2 deletions(-)
 rewrite README.md (100%)
[detached HEAD 128793a] Create a document about git workflow
 Date: Thu Aug 4 09:27:39 2016 +0100
 1 file changed, 266 insertions(+), 2 deletions(-)
 rewrite README.md (100%)
Successfully rebased and updated refs/heads/paulo-is-hobbit.
```

Push your changes.

```
# git push origin paulo-is-hobbit -f
```

```
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 4.17 KiB | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To git@github.com:BrandwatchLtd/paulo-hobbit.git
 + 934751b...128793a paulo-is-hobbit -> paulo-is-hobbit (forced update)
```

Now you can see the branch has no conflicts and it can be merged.

![](/imgs/noconflict.png)

Please, let's be happy and drink some pints now =).

## Conclusion

I'm not a git guru, to be honest I'm a git newbie. I just have
exposed here my experience working with git in different
environments. If you don't like it, stop complaining and start
contributing to make it better. 

"If everyone is moving forward together, then success
takes care of itself." --Henry Ford

