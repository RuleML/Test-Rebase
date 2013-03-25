Test-Rebase
===========

A fresh repository for testing the rebase workflow

Prerequisites
-------------
1. You must have Git installed on your system. See [7].
   
Initialization
--------------
1. Fork to create a public repo in your own Github account. 
I'll use my account (greenTara) for the examples. 
You should replace "greenTara" with your Github user name.

2. Clone your fork to your local computer.([1])

    $ cd path/to/directory/of/Git/repositories  
    $ git clone https://github.com/greenTara/Test-Rebase.git
    
3. Enter the local repository

    $ cd Test-rebase

3. Add the central (RuleML) repository as a read-only remote.([2])

    $ git remote add ruleml git://github.com/RuleML/Test-Rebase.git
    
4. Other configuration steps, such as providing your name and email so your commits can be identified
   should be performed at this point.

    $ git config --global user.name "Tara Athan"
    
    $ git config --global user.email "taraathan@gmail.com"
    
    $ git config --global push.default simple

Modifying the RuleML Website
----------------------------
1. Update your local clone from the ruleml remote.([2])

    $ git pull ruleml master
        
2. Modify your local clone:  
  a) Make your changes in your usual working environment (plain text eclipse, oXygen, ...), and test your modifications  
  b) Optional: If you add or delete files or folders, use  

    $ git add -A

  c) Commit frequently, using messages that are helpful to you,([4], [6])  

    $ git commit -a
    
  d) repeat a-c, or continue to the next step.
    
   
3. When your fix is finished (or far enough along that you want some review), 
  update your repository (again) from the ruleml repo online.([2])
  This time, instead of using "pull" (which is a shortcut for "fetch-merge"), we will use 
  "fetch-rebase.
  Rebase is an alternative to merge that re-writes history regarding the order and granularity of commits.

  a) Fetch from the central RuleML repository:
  
    $ git fetch ruleml master
    
  b) If nothing was fetched, and you made only one or a few commits, you may continue with step 4.
   Otherwise, rebase interactively:
   
    $ git rebase -i ruleml/master

  c) There may be conflicts from this fetch-rebase that need to be resolved at this point.
To avoid such conflicts, maintain communication with other contributors to avoid
simultaneously modifying the same portion of the website.
The github issue-tracker can be used for this purpose.
        
4. Push your commits to your remote fork.([2])

    $ git push origin
    
5. Login to your Github account and perform the following:  
  a) verify that everything got uploaded OK  
  b) submit a pull request to RuleML/Test-Rebase from your Github account.  

6. The RuleML maintainer and/or other developers will make comments on your pull-request if 
anything needs to be changed.
You can push new commits to your local fork and they will automatically be added to the pull-request.
If your pull-request is accepted, your commits will be add to the central RuleML/Text-rebase repository.
They will then be propagated to other forks when Step #1 or Step #3 is 
executed by any user. The RuleML repository will not make announcements of modifecations or create pull-requests.

Diagram
-------

Triangular GITHUB/GIT flow:

        pull request
my fork ---------> central repo         GITHUB
     ^               /
push \             / pull(or fetch/rebase)
         \         v
        local clone                           GIT

GUI Clients
-----------
1. Tortoise Git is capable of all of the above commands, including interactive rebase.

[1]:http://git-scm.com/book/en/Git-Basics-Getting-a-Git-Repository
[2]:http://git-scm.com/book/en/Git-Basics-Working-with-Remotes
[4]:http://git-scm.com/book/en/Git-Basics-Recording-Changes-to-the-Repository
[5]:http://git-scm.com/book/en/Git-Branching-Rebasing
[6]:http://git-scm.com/book/en/Getting-Started-Git-Basics
[7]:http://git-scm.com/book/en/Getting-Started-Installing-Git
