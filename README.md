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
    
Alternative to 3 & 4:
If you are feeling very confident, then you could replace the fetch-rebase sequence with simply

    $ git pull ruleml master
    
Why is this risky? If someone else has pushed to ruleml since your last pull, these changes may conflict with yours.
Doing a fetch is a cautious way to obtain these changes without attempting a merge.
If the fetch doesn't fetch anything, then you could push to origin without bothering with rebase
(provided you don't care about squashing your commits.)

Why is squashing with rebase a good idea? 
The recommended practice for Git is to commit often (many times a day) and push less often
(typically once a day, or at natural breaks). 
If a revert is ever needed, it is easier to review one comprehensive message per push, rather than many separate
short messages. Rebase allows you to generate such a comprehensive message by simply concatenating all the little
commit messages.

Finally, if someone did push since your last pull, the repo history will display a side loop for your
push, rather than a linear history. A nonlinear history is more challenging to unravel.
        
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
