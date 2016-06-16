---
layout: post
title:  "Welcome to Git"
date:   2016-06-16 23:44:37 +0530
comments: true
categories: Introduction to Git
---


 
* * *

* * *

<br>
<br>


If you are using windows, use git-bash (I prefer that).

<br>


Creating a new repository
--------------------------

In your github, select "Create a new repository".

To avoid errors, do not initialize the new repository with README, license, or gitignore files. You can add these files after your project has been pushed to GitHub.


<br>
 
* * *


<br>


Initializing a new repository 
------------------------------

Open terminal for linux, git-bash for windows.

Create a new directory using CLI or GUI,
{% highlight ruby %}
$ mkdir hellogit
{% endhighlight %}

Go to the directory,
{% highlight ruby %}
$ cd hellogit
{% endhighlight %}

 Better to use your newly created repositories name instead of "hellogit".

{% highlight ruby %}
$ git init
{% endhighlight %}

This command will initial a new git repository in the local system. This is will shown in your github repositories until you push it (we look into a little later).


<br>
 
* * *

<br>


Configuring the created repository
-----------------------------------

{% highlight ruby %}
$ git config --global user.name m-nikhil
$ git config --global user.email m_nikhil@outlook.com
{% endhighlight %}

Here the --global flag is optional. Its is used to set the configuration globally, i.e. for repository you are gonna create.

The above configurations state the repository is under 'm-nikhil' user with email 'm_nikhil@outlook.com'.

 
<br>

* * *

<br>

Setting remote repository
--------------------------

{% highlight ruby %}
$ git remote -v
{% endhighlight %}

This list the tracked repositories. Since we have not yet tracked anything, it lists nothing.


Let's add a repository, where the commits (changes done in the local) to be committed/added.
This is needed because a user will hold many repository. So, one has to address 'which repository'.

{% highlight ruby %}
$ git remote add origin https://github.com/m-nikhil/m-nikhil.git
{% endhighlight %}

Replace "https://github.com/m-nikhil/m-nikhil.git" with the url for the remote repository.

In github, open your newly created repository. Then click on the "Clone or download" button (green one) and copy the url. 
This is your remote repository's url, paste this in the above command.

Now do,

{% highlight ruby %}
$ git remote -v
{% endhighlight %}

You will find your repository's url there.

Like this...
{% highlight ruby %}
origin https://github.com/m-nikhil/m-nikhil.git (fetch)
origin https://github.com/m-nikhil/m-nikhil.git (push)
{% endhighlight %}

Here the "origin" points to your repository's url for push and fetch commands (will look at these later).
The "origin" can be replaced by anything. Origin is the commonly used one like foo/bar.

-v flag standfor verbose. This flag is used to show detailed output.

Try,
{% highlight ruby %}
$ git remote
{% endhighlight %}


Now you have successfully created a new repository :)

 

<br>

* * *

<br>

Pushing a change/commit to the created repository
--------------------------------------------------

{% highlight ruby %}
$ git status
{% endhighlight %}

Git status tells if there's any files out there to be added.
Here you will get a response - nothing to be committed.

{% highlight ruby %}
On branch master
nothing to commit (working directory clean)
{% endhighlight %}

Create a file README.md and type any text in it. I go with 
my name :)

{% highlight ruby %}
$ vi README.md
{% endhighlight %}

Or, you can go with file system. Create a new file in current directory, name it README.md, open the file with any text editor and type in any text. Save it!

Now we have edited our repository's content. We shall now see how to push it to the remote repository in github.

Now do,
{% highlight ruby %}
$ git status
{% endhighlight %}

You will get "README.md" marked as untracked file.
{% highlight ruby %}
Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        README.md

nothing added to commit but untracked files present (use "git add" to track)
{% endhighlight %}


Git add prepare the content of files for the next commit.

{% highlight ruby %}
$ git add README.md
{% endhighlight %}

Again do,
{% highlight ruby %}
$ git status
{% endhighlight %}

{% highlight ruby %}
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

        new file:   README.md
{% endhighlight %}

Now "README.md" is a tracked file, which means this file is ready to be committed. If we have 5 files,
we could add only one file and commit it. The other 4 files remains untracked.

Now let us commit it. In git, each change is pushed to the remote repository with a commit. A commit is just a piece of text denoting 'what's the update for' analog to the suject in the email. 

{% highlight ruby %}
$ git commit -m "Initial commit"
{% endhighlight %}

Output:
{% highlight ruby %}
[master (root-commit) 0140141] Inital commit
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
 {% endhighlight %}

Here a commit with name "Initial commit" created. Any suitable name can be given.

This command creates a commit with wrapping the tracked files/added files.

Try,
{% highlight ruby %}
$ git status
{% endhighlight %}

{% highlight ruby %}
On branch master
nothing to commit, working directory clean
{% endhighlight %}

Similar to beginning, you will get nothing to commit because in this stage there's no file left uncommitted.
 
Till now the remote repository in the github is not updated.

The final step,
{% highlight ruby %}
$ git push origin master
{% endhighlight %}

Here, the origin refer to the previously created remote link. And master is the current local branch.
A repository can have many branches i.e. many versions of the code, like one branch to solve a particular issue in the code. 'master' is the main branch. Branch is an important concept in git.

The command pushes the commit from master to the origin.Once the command is ran. You can view the changes in the github.

If you make anychanges to the README.md file, again you need to add and commit it.Finally push to the remote repository.

If you have many files/folders to be added. Instead of each one by their name, you can do
{% highlight ruby %}
$ git add .
{% endhighlight %}
This command will add all the files/folders created/updated in the local repository.


NOTE: You cannot add a empty folder as a change to repository. Git does not recognize it as a change.
But a empty file can be added and committed.











