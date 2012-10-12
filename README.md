Test-Rebase
===========

A fresh repository for testing the rebase workflow

Initialization
--------------
1. Fork to create a public repo in your own account. I'll use my account (greenTara) for the examples. 
You should replace "greenTara" with your Github user name.

2. Clone your fork to your local computer

    $ git clone https://githubcom/greenTara/Test-Rebase.git

3. Add the central (RuleML) repository as a read-only remote [1]

    $ git remote add ruleml git://github.com/RuleML/Test-Rebase.git

Branching to Resolve Issues
---------------------------
1. Synchronize your master branch with the ruleml remote

    $ git checkout master
    
    $ git pull ruleml master
    
2. There should be no conflicts from this pull, because you have been following the
  workflow described here and doing all your development in temporary branches.
    
3. Select an issue from the issue tracker to work on, or create a new issue.

4. Create and switch to a new branch in your local repo, with name, say, Issue#45.

    $ git checkout -b Issue#45 

5. Make your changes in your usual working environment (eclipse, oXygen, ...),
   commit frequently, using messages that are helpful to you, 
       
    $ git commit -a

    test, repeat, ..., but do NOT push to your public fork. 
    If you add or delete files or folders, use

    $ git add -A
    
    before you commit. End with a commit.
   
6. When your fix is finished (or far enough along that you want some review), 
  update your repository from the ruleml repo online. 

    $ git fetch ruleml
    
7. Use rebase to reorder your commits to occur on top of everybody else's. 
   The -i option allows you to interactively clean up your commits.

    $ git rebase -i ruleml/master
    
8. Push your commits to a new branch in your remote fork

    $ git push origin Issue#45
    
9. Login to your Github account to verify that everything got uploaded OK, then
submit a pull request to RuleML/Test-Rebase from your Github account.
If the RuleML repo already has a branch for Issue#45, submit your pull-request to that branch,
otherwise submit to master.

10. The RuleML maintainer will make comments on your pull-request if anything needs to be changed.
You can push new commits to your Issue#45 branch and they will automatically be added to the pull-request.
If your submission is accepted, the RuleML/Issue#45 branch will be merged with RuleML/master.
It will then be propagated to all forks when Step #1 or Step #6 are executed.
                 
[1]:http://git-scm.com/book/en/Git-Basics-Working-with-Remotes     

