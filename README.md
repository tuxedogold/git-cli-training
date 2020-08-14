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
