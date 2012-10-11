Test-Rebase
===========

A fresh repository for testing the rebase workflow

Initialization
--------------
1. Fork to create a public repo in your own account. I'll use my account (greenTara) for the examples. You should replace "greenTara" with your Github user name.

2. Clone your fork to your local computer

    $ git clone https://githubcom/greenTara/Test-Rebase.git


3. Add the central (RuleML) repository as a read-only remote

    $ git remote add ruleml git://github.com/RuleML/Test-Rebase.git

Branching to Resolve Issues
---------------------------
1. Synchronize your master branch with the ruleml remote

    $ git checkout master
    
    $ git pull ruleml master
    
2. if conflicts arise from the pull, fix these in your local checkout and commit

    $ git commit -a    
    
3. Select an issue from the issue tracker to work on, or create a new issue.

4. Create and switch to a new branch in your local repo, with name, say, Issue#45.

    $ git checkout -b Issue#45 

5. Make your changes in your usual working environment (eclipse, oXygen, ...),
   commit frequently, using messages that are helpful to you, 
       
    $ git commit -a

test, repeat, ...
   
6. When you are satisfied with your fix, "merge" back into your master branch
using rebase to squash your many commits into a single commit

    $ git rebase -i Issue#45
    
    $ git checkout master
    
    $ git merge Issue#45

7. Update your repository's master branch from the ruleml repo

    $ git fetch ruleml
    
8. Reorder your commits to occur on top of everybody else's

    $ git rebase ruleml/master
    
9. Push your commits to your remote fork

    $ git push origin
    
10. Submit a pull request to RuleML/Test-Rebase

    $ git request-pull origin/master git://github.com/RuleML/Test-Rebase.git
                 
References
----------
http://git-scm.com/book/en/Git-Basics-Working-with-Remotes     

