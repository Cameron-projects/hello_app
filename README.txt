October 04, 2020
================

Working in the AWS Cloud9 environment requires re-configuration after restarting 
the EC2 Server Instance.  The Ruby on Rails Tutorial book requires the following
commands:

To restart:
 - login to console.aws.amazon.com 
 - User "Administrator"
The Cloud9 development environments are displayed on the login dashboard
 - Click "Start IDE" on the Ruby2 Environment
Once the IDE is restarted 
 - open two separate Terminal tabs and run the following commands in both:

# Set up command Aliases
alias ll='ls -l'

# Move into the development directory
cd ~/environment/hello_app

# Check the version of rails - It should be 6.0.2.1
rails -v

# Check the version of ruby
#    it should be: ruby 2.6.3p62 (2019-04-16 revision 67580) [x86_64-linux]
ruby -v

# Check the version of Heroku
#    it should be: heroku/7.43.2 linux-x64 node-v12.16.2
heroku --version

# Update the Yarn files (this program manages software dependencies.
yarn install --check-files

# Validate the Git configuration
# and if not the corrections should be made using:
#     git config --global ....
#     git config --local ....
#
# It should look like:
#   credential.helper=cache --timeout= 86400
#   credential.usehttppath=true
#   core.editor=/usr/bin/nano
#   alias.co=checkout
#   user.name=Cameron
#   user.email=cameron@vericatch.com
#   core.repositoryformatversion=0
#   core.filemode=true
#   core.bare=false
#   core.logallrefupdates=true
#   remote.origin.url=https://github.com/Cameron-projects/hello_app.git
#   remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
#   branch.master.remote=origin
#   branch.master.merge=refs/heads/master
#   remote.heroku.url=https://git.heroku.com/afternoon-waters-65915.git
#   remote.heroku.fetch=+refs/heads/*:refs/remotes/heroku/*
git config -l

# In the second terminal tab start the rails server, this is a blocking program
rails server

# back to the first or working terminal tab
# open the browser to the Ruby app by clicking on the overlaying squares in the
#   browser tab of the IDE (top right corner).  A new browser tab will open with
#   the execution of the appication, hello_app

# DEVELOPMENT
# -----------

# create a new branch
git checkout -b <new_branch_name>

# Change branches
git checkout <branch_name>

# To see all the branches and determine which one you're working on
#   The branch with the star is the one you're currently working on
git branch

# Edit code 

# determine what has changed from the original source
git status

# add modified files to a staging area prior to commiting them
git add -A -m "<message about changes>"

# or if you've NOT added any new files you can use:
git commit -a -m "<message>"

# if you need to delete one of the added files
git rm --cached <file1> <file2> ...

# commit the added files
git commit -m "<message about changes>"

# to see all commit messages
git log

# if all is good at this point you will merge the changes back to the master branch
git checkout master
git merge <branch_name>

# push the changes back to the github repo
git push

# login to Heroku
heroku login --interactive

# push the code from github to heroku to deploy
git push heroku master

