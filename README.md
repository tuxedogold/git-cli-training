# git CLI quick reference/practice

First, fork this project within github 

Clone a repo to test it out 

`git clone git@github.com:[yourgithubprofile]/git-cli-training.git`

If you haven't set up your ssh key, this won't work so try creating a key using ssh-keygen and uploading 
your public key to github

`ssh-keygen -t rsa -b 4096 -C "your_email@example.com" `

This key authenticates you on the server. you can locate it in your user directory:

`
cd %UserProfile%/.ssh/
dir
`
you are looking for a file that ends in .pub


Setup some identifying information for your commit history

`git config --global user.name "[yourname]"`
then run 
`git config --global user.email "[youremail@email.com]"`

## Working off of master/ basic git commands

create a file or make some changes to represent some code changes

`ping google.com > a.out`

now type

`git status`

It should tell you that a.out is a new file and is untracked by git, so lets change that

`git add a.out`

Note, you can also write

`git add .`

where . is a wildcard for all files in your folder. if you do this, be sure to use the status command to confirm you only added what you want

Great! Now lets tell git that this is a good milestone in our "code" by committing

`Git commit -m “add a.out”`

now try the git status command to confirm the changes have been sent to git.

Next, lets get ready to send these changes to the server. Always pull before pushing to update your local code

`git pull`


Send your code to the server!

`git push`


# topic/feature branching
lets see what branches we have

`git branch`

looks like we are on master, you can tell by the *. If you have more branches, you would see them in the list without a star

Lets make a new branch!

`git checkout -b "123-very-descriptive-branchname"`

now try the command below, you should observe that you are no longer on master

`git branch`

Lets change some "code" for our branch. 

`ping amazon.com > am.txt`

Lets see what has changed our "source file" am.txt

`git diff`

turning it up anotch, this command will tell git about all your new changes and commit all in one!
`git add -A & git commit -m "update a.txt to microsoft" `

Thats great, but its a lot to type, so lets turn it up again.

`ping microsoft.com > a.txt`

Lets see what has changed our "source file" a.txt

`git diff`

Since git already knows about a.txt from our very first commit, we can use a shortcut

`git commit -am "change ping request from google to microsoft"`

When you do git diff, you should not see any changes since we commit them already

to see the changes of your most recent commit, try

`git show`

We've done a lot of committing. Lets take a look at the history

`git log`

Great work! almost there!

Lets check on our files one more time to be sure

`git status`

For any reason lets say that you didn't want to commit this change, perhaps the reqs changed, maybe you commit something you didn't mean to,
forgot to code review prior to committing, or this code was meant for another branch.

The following command will undo your last commit.
## do not do this if you have pushed the commit

now check your git status and git log. You should find your commit is not there, and you have all your changes back.

Lets say you want these changes, but just not now. type

`git stash`

this stores all of your changes in a stack. check git status and log, the changes are not there and there is no commit

to get them back type

`git stash pop`

All your uncommitted changes are here. Okay, enough toying around. Commit all the changes and lets get them to the server

`git push`

If this is your first push on this branch, type

`git push --set-upstream origin 123-very-descriptive-branchname`

Okay, at this point we are ready to make a pull-request on the server. in github/gitlabs you will see a url, you can simply click that url and fill out your info. However, in azure devops you will have to browse on your own or use other utilities to do so :-)


Okay, now lets say someone has pushed more code to origin master..
Merge those changes into your branch with the pull command. You could simulate this by changing to master and commiting, then pushing changes

`git pull origin master`

Now you have the changes, check the log. This will bring in new changs on top of your commits

If everything looks good, go ahead and push your branch back to the cloud

`git push`


Once your pull request is complete, delete your branch locally by first switching back to master and then running the branch command with -d

`git checkout master`


`git branch -d localBranchName`

