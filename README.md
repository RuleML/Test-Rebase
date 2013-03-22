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

Modifying the RuleML Website
----------------------------
1. Update your local clone from the ruleml remote.([2])
    
    $ git pull ruleml master
        
2. Make your changes in your usual working environment (eclipse, oXygen, ...),
   commit frequently, using messages that are helpful to you,([4], [6]) 
       
    $ git commit -a

    test, repeat, ..., but do NOT push to your public fork. 
    If you add or delete files or folders, use

    $ git add -A
    
    before you commit. End with a commit.
   
3. When your fix is finished (or far enough along that you want some review), 
  update your repository from the ruleml repo online.([2]) 

    $ git fetch ruleml master

    There may be conflicts from this pull that need to be resolved at this point.
    To avoid such conflicts, maintain communication with other contributors to avoid
    simultaneously modifying the same portion of the website.
    The github issue-tracker can be used for this purpose.

4. Use rebase to reorder your commits to occur on top of everybody else's. 
   The -i option allows you to interactively clean up your commits.([5])

    $ git rebase -i ruleml/master
    
5. Push your commits to your remote fork.([2])

    $ git push origin
    
6. Login to your Github account to verify that everything got uploaded OK, then
submit a pull request to RuleML/Test-Rebase from your Github account.

7. The RuleML maintainer and/or other developers will make comments on your pull-request if 
anything needs to be changed.
You can push new commit to your local fork and they will automatically be added to the pull-request.
If your submission is accepted, your commits will be add to the central RuleML/Text-rebase repository.
It will then be propagated to all forks when Step #1 or Step #3 is 
executed by any user.

[1]:http://git-scm.com/book/en/Git-Basics-Getting-a-Git-Repository
[2]:http://git-scm.com/book/en/Git-Basics-Working-with-Remotes
[4]:http://git-scm.com/book/en/Git-Basics-Recording-Changes-to-the-Repository
[5]:http://git-scm.com/book/en/Git-Branching-Rebasing
[6]:http://git-scm.com/book/en/Getting-Started-Git-Basics
[7]:http://git-scm.com/book/en/Getting-Started-Installing-Git
