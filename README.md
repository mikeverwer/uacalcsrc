# uacalcsrc

This is the main repository for the source code of the [Universal Algebra
Calculator](http://uacalc.org) (UACalc).

For the GUI version of the program, please visit
the [UACalc webpage (uacalc.org)](http://uacalc.org).

--------------------------------------------------

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Contents**

  - [Importing, browsing, and collaborating](#importing-browsing-and-collaborating)
    - [Browsing the source code](#browsing-the-source-code)
    - [Contributing using fork and pull requests](#contributing-using-fork-and-pull-requests)
    - [Importing uacalcsrc into Eclipse](#importing-uacalcsrc-into-eclipse)
    - [Updating your fork](#updating-your-fork)
  - [The UACalc API](#the-uacalc-api)
    - [Using UACalc packages in your own software](#using-uacalc-packages-in-your-own-software)
  - [Bugs and Other Issues](#bugs-and-other-issues)
  - [History](#history)
  - [Citing UACalc](#citing-uacalc)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Importing, browsing, and collaborating

The page is meant to provide some hints and advice about downloading, importing,
browsing, and modifying the source code in the uacalcsrc repository. Much of it
concerns the use of git and GitHub, and there are plenty of better sources
for this information, such as the [GitHub help pages](https://help.github.com/).

The instructions below will require entering commands in a terminal
window with some sort of Unix style shell, like bash.
If you will be copying the repository to your local machine, these steps
assume the repository lives in a directory called `~/git/uacalcsrc`, so
this first command creates a `~/git` directory, if it doesn't already exists
(and does nothing if it does exist):

    $ mkdir -p ~/git

### Browsing the source code

If you merely want to browse the UACalc source code, you can do so using the
GitHub webpages, or you can
[clone](https://help.github.com/articles/fetching-a-remote/) the repository to
your local drive with a command like:

    $ git clone git@github.com:UACalc/uacalcsrc.git ~/git/uacalcsrc

or

    $ git clone https://github.com/UACalc/uacalcsrc.git ~/git/uacalcsrc


### Contributing using fork and pull requests

If you expect to contribute improvements to the source code, instead of cloning
directly it is advisable to first
[fork](https://help.github.com/articles/fork-a-repo/) the repository to your own
GitHub account, and then clone your own fork.  To do so, login to your GitHub account,
navigate to the [UACalc/uacalcsrc](https://github.com/UACalc/uacalcsrc)
repository, then click the
[Fork link](https://github.com/UACalc/uacalcsrc#fork-destination-box) on the
upper right.  Once the fork is created, clone the forked repository to your
local drive with a command like

    $ git clone git@github.com:your-user-name/uacalcsrc.git ~/git/uacalcsrc

or

    $ git clone https://github.com/your-user-name/uacalcsrc.git ~/git/uacalcsrc

Now you can modify the source code as you wish and then, if you want to
recommend that your changes be incorporated into the main UACalc/uacalcsrc
repository, you should follow these steps:

1. Commit your changes to your local repository (with an informative commit
   message!).

        $ git commit -m "fixed a bug in the bar method of the Foo class"

2. Push the changes to your remote repository (i.e., to the fork you created above).

		$ git push origin master

3. [Create a pull request](https://help.github.com/articles/creating-a-pull-request/)
   by navigating to your fork's GitHub page and clicking the `Pull
   Request` link (which appears next to a message like, "This branch is 1 commit
   ahead of UACalc:master").

   Be sure to include an informative comment justifying the
   recommendation to merge your changes into the main respository.

To keep your fork current with the main UACalc/uacalcsrc repository, see the
section [Updating your fork](#updating-your-fork) below.

### Importing uacalcsrc into Eclipse or IntelliJ

There are a number of ways to import this repository into the
[Eclipse IDE](http://www.eclipse.org/) or [IntelliJ IDEA](https://www.jetbrains.com/idea/). 
One such method is described in this section.

1. Create your own fork of the repository, as explained in the [previous section](#contributing-using-fork-and-pull-requests).

2. Clone your fork of the repository to your local drive.

            git clone git@github.com:your-user-name/uacalcsrc.git ~/git/uacalcsrc
   or
            git clone https://github.com/your-user-name/uacalcsrc.git ~/git/uacalcsrc


  
3. **Import into Eclipse** (for IntelliJ IDEA skip to step 4.)

   + Launch Eclipse and use the File menu to import the source code:

            File --> Import --> Git --> Projects from Git

     then click Next.

   + Select `Local`, click Next, then click Add and browse to the directory where
     you clone the repository in Step 1 above (e.g., `~/git/uacalcsrc`).

   + Select the `uacalcsrc` repository and click Next.

   + Select the `Import existing project` radio button, click Next, and then
     select the algebra project and click finish.

4. **Import into IntelliJ IDEA**

   + Launch IDEA and close any open projects to get to the main welcome 
     screen.

   + Select `Import Project` and then navigate to the `uacalcsrc` 
     directory (the location of your fork of the `uacalcsrc` repository).

   + With `uacalcsrc` selected, click the `OK` button.

   + On the "Import Project" page, choose 
     "Import project from External Model" 
     and choose `Eclipse` and click next.

*This section is under construction.*

### Updating your fork

When improvements are made to the "upstream" UACalc/uacalcsrc repository,
you will probably want to update your fork to incorporate these
changes.  Below is a list of the commands that accomplish this, but see
[this page](https://help.github.com/articles/configuring-a-remote-for-a-fork/) and
[this page](https://help.github.com/articles/syncing-a-fork/)
for more details.

1. Change to the working directory of your local copy of the repository and
   specify the upstream repository.

        $ cd ~/git/uacalcsrc
        $ git remote add upstream git@github.com:UACalc/uacalcsrc.git

2. Verify that it worked.

        $ git remote -v

   The output should look something like this:

        origin	git@github.com:your-user-name/uacalcsrc.git (fetch)
        origin	git@github.com:your-user-name/uacalcsrc.git (push)
        upstream	git@github.com:UACalc/uacalcsrc.git (fetch)
        upstream	git@github.com:UACalc/uacalcsrc.git (push)

   If the foregoing fails, try

        git remote add upstream https://github.com/UACalc/uacalcsrc.git


3. In the working directory of your local project, fetch the branches and their
   respective commits from the upstream repository.

        git fetch upstream

4. Check out your fork's local master branch.

        git checkout master

5. Merge the changes from upstream/master into your local master branch. This
   brings your fork's master branch into sync with the upstream repository,
   without losing your local changes.

        git merge upstream/master

6. Finally, do

        git commit -m "merged changes from upstream"
        git push origin master

   and check that the GitHub page for your fork's repo shows the message,
   "This branch is even with UACalc:master."

7. If there are other branches besides `master` that you want to update, repeat
   steps 4--6, replacing `master` with another branch name.

-----------------------------------------

## The UACalc API

### Using UACalc packages in your own software
It's possible to write programs in Scala or Jython
(and probably other languages that runs on the jvm) that import
and make use of java packages that make up the UACalc.
Here we show how to obtain the UACalc jar files
and then give an example demonstrating how to use the jars
and import UACalc packages into a Scala project
using the IntelliJ Idea IDE. Something similar should work
for other languages (e.g., Jython) in other IDEs (e.g., Eclipse).

1. **Getting the jar files.**
   There are two ways to do this.  (You only need to do one of these---A or B, not both.)

   + **A. Download precompiled jars.**  
     If you just want pre-compiled (and possibly a bit out-of-date) versions of uacalc.jar and other jars, you can
     try invoking the following at the command line:

           wget http://uacalc.org/uacalc.jar

     (If you don't have the `wget` program, then you could try pasting http://uacalc.org/uacalc.jar into the address field of your web browser; your browser should ask you where you want to save the `uacalc.jar` file.)

     You can download other supporting jar files you might need from the links on [this page](http://www.uacalc.org/download/), or copy and paste the following into a terminal on a computer that has the `wget` program installed:

           wget http://uacalc.org/download/designgridlayout-1.1p1.jar
           wget http://uacalc.org/download/groovy-all-1.0.jar
           wget http://uacalc.org/download/groovy-engine.jar
           wget http://uacalc.org/download/miglayout-3.7-swing.jar
           wget http://uacalc.org/download/swing-layout-1.0.2.jar

   + **B. Roll your own.**  
     Clone the uacalcsrc repository, e.g.,

          git clone git@github.com:UACalc/uacalcsrc.git

     Compile the code (see [these instructions](http://uacalc.org/download/) for more info)

          cd uacalcsrc
          ant dist

     (You must install the `ant` program if you don't have it already; on an Ubuntu Linux box, do `sudo apt install ant`)

     If the `ant dist` command above succeeds then all of the jar files should now be in the `../dist/lib` directory.

## Bugs and Other Issues
If you think you found a bug in the calculator, if you encounter a problem with
the instructions on this page, or if you have any other issue that you'd like to
call attention to, please
[create a new issue](https://github.com/UACalc/uacalcsrc/issues).

## History

This git repository was initially created on 2014 Nov 25 by importing Ralph
Freese's uacalcsrc cvs repository from sourceforge using the following command:

    git cvsimport -C ~/git/uacalcsrc -r cvs -k -v -d :pserver:anonymous@uacalc.cvs.sourceforge.net:/cvsroot/uacalc -A authorfile.txt uacalcsrc

Before issuing the above `git cvsimport` command the git-cvs package must be
installed (e.g., `sudo apt-get install git-cvs`)
**General Notes**

The authorfile.txt contains names and email addresses of authors who
contributed to the cvs source tree. This is needed in order to preserve the
contribution in the resulting git repo.

**Eclipse Notes**
To import the source code in Eclipse, follow these steps:

1. First clone the repository to your local drive with something like

        git clone https://github.com/UACalc/uacalcsrc.git ~/git/uacalcsrc

2. Open Eclipse and use the File menu to import the source code:

        File --> Import --> Git --> Projects from Git

   then click Next.

3. Select `Local`, click Next, then click Add and browse to the directory where
   you clone the repository in Step 1 above (e.g., ~/git/uacalcsrc).

4. Select the uacalcsrc repository and click Next.

5. Select the `Import existing project` radio button, click Next, and then
   select the algebra project and click finish.

## Citing UACalc

If you are using BibTeX, you can use the following BibTeX entry to cite UACalc:

    @misc{UACalc,
      author =      {Ralph Freese and Emil Kiss and Matthew Valeriote},
      title =       {Universal {A}lgebra {C}alculator},
      note =        {Available at: {\verb+www.uacalc.org+}},
      year =        {2011},
    }
