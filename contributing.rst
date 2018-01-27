Contributing to this documentation
==================================

The source code for this documentation is hosted here: https://github.com/holdymoldy/arjuna. It is written in reStructuredText. To contribute to the documentation, you'll need a basic understanding of git and rst (http://docutils.sourceforge.net/rst.html).

The project is structured to have a single "root" file and arbitrarily many "branch" files. In this project, the "root" file is called "index.rst". The "branch" files all have the ending ".rst". If you want to add a new page, your file must be named with a ".rst" extension. Then, the name of this file must be added to "index.rst" so that it is included in the tree structure during compilation. For example, if I create a file called "arjuna_facts.rst", I have to include "arjuna_facts" in the "index.rst" file.

Git
---

Git is a code version control system. If you're interested in using git for projects other than this documentation, you can learn the basics here: https://git-scm.com/. To contribute to the documentation, you will only need to know a few basic commands.

Git workflows are based on changing a "remote" code base (called a repo) by making "local" changes (such as on your own computer), then adding your code to the remote code base (called "pushing"). **Because you do not have write access to this code base, you will need to "fork" the code and make a pull request.** 

First, create a fork of the code base. Go to https://github.com/holdymoldy/arjuna, and in the upper right-hand corner click "Fork". This will create a copy of the documentation on your github account. Now clone your code base on your local machine: on a terminal window, type the following "git clone" command (replacing your username) and cd into this folder:

.. code-block:: bat

	> git clone https://github.com/your_username/arjuna.git
	> cd arjuna

Now, check to make sure your code base is up to date:

.. code-block:: bat
	
	> git fetch

If it is not, "pull" these changes onto your local code base:

.. code-block:: bat

	> git pull

After you make some changes, you will need to make a "commit." A commit is basically a series of changes to the code which are tagged and trackable. First add some files to your commit:

.. code-block:: bat

	> git add files_changed

Then create a commit:

.. code-block:: bat
	
	> git commit -m "I have made changes to file1, file2, etc."

Finally, push this commit to your fork:

.. code-block:: bat
	
	> git push

If you go onto the webpage of your fork, you will see that your commit has changed the codebase. However, this is *your* codebase, while the documentation is built from holdymoldy's code base. Therefore, you will need to submit a pull request to this page. This is an easy procedure, and instructions are here: https://help.github.com/articles/creating-a-pull-request/

Once we've looked at your changes, the documentation will be rebuilt to reflect your contributions.

RST
---

RST is a plaintext markup syntax and parser system. It is very easy to learn and use. To contribute to this documentation, your contributions must be written in RST. Easy-to-follow guides can be found here: http://docutils.sourceforge.net/rst.html.

