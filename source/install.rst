.. _setup:

Installing oTree
================

Important note
--------------

If you publish research conducted using oTree,
you are required by the oTree license to cite
`this paper <http://dx.doi.org/10.1016/j.jbef.2015.12.001>`__.
(Citation: Chen, D.L., Schonger, M., Wickens, C., 2016. oTree - An open-source
platform for laboratory, online and field experiments.
Journal of Behavioral and Experimental Finance, vol 9: 88-97)

Step 1: Install Python
----------------------

oTree requires Python 3.4 or higher.

If you already have Python 3.x installed
(check by entering ``pip3 -V`` at your command prompt),
you can skip the below section. Or, uninstall your existing version of Python,
and proceed with the below steps.

Step 1: Install Python 3.6 (for Windows users)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Download and install `Python 3.6 <https://www.python.org/downloads/release/python-360/>`__.
(Python 3.4 and 3.5 are also OK.)
Check the box to add Python to PATH:

.. figure:: _static/setup/py-win-installer.png

Once setup is done, search in your Windows Start Menu for the program "PowerShell",
open PowerShell, and enter ``pip3 -V``:

.. figure:: _static/setup/powershell.png

It will output a line that gives the version of Python at the end;
this should match the version of Python you just installed:


Step 1: Install Python 3.6 (for macOS users)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You need to install Python 3.4 or higher. We recommend installing it with Homebrew.
(However, if you already have Python 3.6 installed through Conda, that should be OK.)

* In Finder, search for and open the "Terminal" app:

.. figure:: _static/setup/macos-terminal.png


* In the terminal window, type this and hit enter:

.. code-block:: bash

    xcode-select --install

When prompted, select to install the "command line developer tools".

* Then install `Homebrew <http://brew.sh/>`__:

.. code-block:: bash

    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

* Update your ``PATH`` variable to state that homebrew packages should be
  used before system packages::

    echo "export PATH=/usr/local/bin:/usr/local/sbin:\$PATH" >> ~/.bash_profile

* Reload ``.bash_profile`` to ensure the changes have taken place::

    source ~/.bash_profile

* Install python::

    brew install python3

* Then test that it worked::

    pip3 -V

It will output a line that gives the version of Python at the end;
this should match the version of Python you just installed.

Step 1: Install Python 3.6 (for Linux/Unix users)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

We recommmend installing using your system's package manager to install Python 3.6.
If ``Twisted`` fails to compile, install the ``python-dev`` package (e.g. through ``apt-get``).

More information in the :ref:`Linux server setup <server-ubuntu>` section.

Step 2: Install oTree
~~~~~~~~~~~~~~~~~~~~~

Enter this in PowerShell (Windows) or Terminal (macOS):

.. code-block:: bash

    pip3 install -U otree-core

.. note::

    If you get this Windows error about Twisted and ``vcvarsall.bat``::

        error: Microsoft Visual C++ 9.0 is required (Unable to find vcvarsall.bat). Get it from http://aka.ms/vcpython27

    To fix this, install the `Visual C++ Build Tools <http://go.microsoft.com/fwlink/?LinkId=691126>`__.


Step 3: Run oTree
~~~~~~~~~~~~~~~~~

Open PowerShell (on Windows) or Terminal (on macOS), and run::

    otree startproject oTree

If it's your first time, we recommend choosing the option to include the sample games.

The above command will create a folder named ``oTree`` in your home directory.
(If you want, you can move the folder to another location.)

Then change to the directory you just created::

    cd oTree

.. note::

    If you've never used a command prompt like Terminal or PowerShell,
    basically all you need to know is it is an alternative
    to your file explorer (or Finder on Mac). Instead of clicking on files
    and folders, you type commands to navigate folders and execute programs.

    Here are some useful commands:

    -   ``pwd``: shows what folder you are currently in
    -   ``ls``: lists the files and subfolders in the current folder
    -   ``cd``: move to a subfolder. For example, ``cd oTree`` takes you to the subfolder ``oTree``.

Reset the database::

    otree resetdb

(You might see a message about migrations; you can ignore that.)

Then run the server::

    otree runserver

.. note::

    If Python crashes when you run this command,
    and you're using PowerShell, try using CMD instead
    (search your start menu for "Command Prompt")

Then open your browser to `http://127.0.0.1:8000/ <http://127.0.0.1:8000/>`__.
You should see the oTree demo site.

To stop the server, enter ``Control + C`` at your command line.
To restart the server from the command line, pressing your keyboard's "up" arrow (this will retrieve the last command you entered),
and hit Enter.

.. _pycharm:

Step 4: Install a Python editor (PyCharm)
-----------------------------------------

You will need a text editor to write your Python code.

We recommend using `PyCharm <https://www.jetbrains.com/pycharm/download/>`__.
Professional Editon is better than Community Edition because it makes
Django programming easier.
PyCharm Professional is free if you are a student, teacher, or professor.

Even if you normally use another text editor,
we recommend at least trying PyCharm, because PyCharm's autocompletion
makes learning oTree much easier:

.. figure:: _static/setup/pycharm-autocomplete.gif

Once you have installed PyCharm,
go to "File -> Open..." and select the folder you created with ``otree startproject``.

Then click on ``File –> Settings`` (or ``Default Settings``) and navigate to ``Languages & Frameworks -> Django``,
check "Enable Django Support" and set your oTree folder as the Django project root,
with your ``manage.py`` and ``settings.py``:

.. figure:: _static/setup/pycharm-django.png

If PyCharm displays this warning, select "Ignore requirements":

.. figure:: _static/setup/pycharm-psycopg2-warning.png

Command line tips & tricks
--------------------------

Here are some tips to using PowerShell (for Windows users) or Terminal (for macOS users):

A few tips:

* You can retrieve the previous command you entered by pressing your keyboard's "up" arrow
* If you get stuck running a command, you can press ``Control + C``.
* In PowerShell, you should right-click to paste a command.

.. _upgrade:

Upgrading/reinstalling oTree
----------------------------

The oTree software has two components:

-  oTree-core: The engine that makes your apps run
-  oTree library: the folder of sample games and other files (e.g. settings.py) that you download from `here <https://github.com/oTree-org/oTree>`__ and customize to build your own project.

.. _upgrade-otree-core:

Upgrade oTree core
~~~~~~~~~~~~~~~~~~

We recommend you do this on a weekly basis,
so that you can get the latest bug fixes and features.
This will also ensure that you are using a version that is consistent with the current documentation.

Run:

.. code-block:: bash

    pip3 install -U otree-core
    otree resetdb

Upgrade oTree library
~~~~~~~~~~~~~~~~~~~~~

Run ``otree startproject [folder name]``. This will create a folder with the specified name and
download the latest version of the library there.

If you originally installed oTree over 5 months ago,
we recommend you run the above command and move your existing apps into the new project folder,
to ensure you have the latest ``settings.py``, etc.