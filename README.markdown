Getting Git
-----------
If you don't you can install it from downloads on the git homepage or you can
install [Github's git GUI](https://help.github.com/articles/set-up-git/).

Setup
-----

    $ git config --global core.editor vim
You may want to fork (create your own copy of) the project on github and
clone from your own repo. You can find the fork button at the top right of
the screen on a github repository, or more help about doing that [here](https://help.github.com/articles/fork-a-repo/).

Branching
----------------
Branching is an essential part of working on a  codebase with other developers. 
It allows you to work on your own copies of the code independently before "**merging**" them together, preventing your work from messing up mine.
Let's create our first branch. Name it after yourself; mine will be `owen-mariani`

    $ git branch owen-mariani
    $ git checkout owen-mariani 
    $ git branch

1. We created a branch
2. We switched into the branch
3. We checked what branch we were on
 
Now, let’s try adding a file into the project. 
Let’s create a text file named after you. For me it is `owen.txt` 
Adding, Commiting, and Pushing
----------------
- In Git, you first add content to the **staging area** by using `git add`.
- To make it official **locally** `git commit`. 
- To make it true throughout **upstream** (the whole repo) `git push`.
Adding
----------------
    $ git add owen.txt

We can see if it worked by checking the `status` of our git repo

    $ git status
    $ git commit -m "Added owen.txt"
files in the previous section. 
    Author: owenmariani 
    Date:   Sun Mar 29 16:13:42 2024 +1200
        Added owen.txt
This tells us all we need to know about the commit
Let's say we committed and we realized it was a mistake, we can easily fix this by doing one of the following:
If we wanted to **go back a certain number of commits**, we can easily just replace 1 with the number we want to go back.
    $ git reset --hard HEAD~1
If there is **a certain commit we want to go back to** we can search for the commit hash and copy and paste it in:
    
    $ git log
    $ git reset --hard <sha1-commit-id>
    
Or if we **just want to look at a previous commit** we can assign it to HEAD doing the following:
    
    $ git checkout <sha1-commit-id>
We now want to merge our `owen-mariani` branch into `main`. First, switch to
the `main` branch.
    git checkout main
Next, we merge the `owen-mariani` branch into `main` :
    $ git merge owen-mariani
**You have to be in the branch you want merge *into*** and then you always
We now practice fixing merge conflicts. Recall that conflicts are caused
You should see a `conflict` with the `mergeConflict.txt` file. This means that
and the broken branch. The output below basically tells you the current
    Auto-merging mergeConflict.txt
If you open the `mergeConflict.txt` file, you will see something similar as
    $ cat mergeConflict.txt
    >>>>>>> broken
The bottom half is the version that is present from the `broken` branch.
For example, I might decide to choose the version from the `broken`
better and move them all above the `======`
    $ git add mergeConflict.txt