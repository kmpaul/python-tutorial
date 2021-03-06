.. title: yourfirst
.. slug: yourfirst
.. date: 2020-04-08 14:29:40 UTC-06:00
.. tags:
.. category:
.. link:
.. description:
.. type: text
.. hidetitle: True
.. has_math: True

.. role:: bash(code)
   :language: bash

.. role:: python(code)
   :language: python

=========================================
Your First Python Tutorial for Scientists
=========================================

Welcome to Your First Python tutorial for scientists! In this self-paced
course you will learn how to write Python code using Python best practices.
Through these instructions you will develop Python scripts and use Git and
GitHub to save and organize your work.  At the end of this tutorial you will
have a grasp of how to begin building your own library of Python tools for
your scientific analysis workflows.

-----------
Why Python?
-----------

You're already here because you want to learn to use Python for your data
analysis and visualizations. Python can be compared to other high-level,
interpreted, object-oriented languages, but is especially great because it is
free and open source!

High level languages:
    Other high level languages include MatLab, IDL, and NCL. The advantage of
    high level languages is that they provide functions, data structures, and
    other utilities that are commonly used, which means it takes less code to
    get real work done. The disadvantage of high level languages is that they
    tend to obscure the low level aspects of the machine such as: memory use,
    how many floating point operations are happening, and other information
    related to performance. C and C++ are all examples of lower level
    languages. The "higher" the level of language, the more computing
    fundamentals are abstracted.

Interpreted languages:
    Most of your work is probably already in interpreted languages if you've
    ever used IDL, NCL, or MatLab (interpreted languages are typically also
    high level). So you are already familiar with the advantages of this: you
    don't have to worry about compiling or machine compatability (it is
    portable). And you are probably familiar with their deficiencies: sometimes
    they can be slower than compiled languages and potentially more memory
    intensive.

Object Oriented languages:
    Objects are custom datatypes. For every custom datatype, you usually have
    a set of operations you might want to conduct. For example, if you have an
    object that is a list of numbers you might want to apply a mathematical
    operation, such as sum, onto this list object in bulk. Not every function
    can be applied to every datatype; it wouldn't make sense to apply a
    logarithm to a string of letters or to capitalize a list of numbers. Data
    and the operations applied to them are grouped together into one object.

Open source:
    Python as a language is open source which means that there is a community
    of developers behind its codebase. Anyone can join the developer community
    and contribute to deciding the future of the language. When someone
    identifies gaps to Python's abilities, they can write up the code to fill
    these gaps. The open source nature of Python means that Python as a
    language is very adaptable to shifting needs of the user community.

Python is a language designed for rapid prototyping and efficient programming.
It is easy to write new code quickly with less typing.

----------------------------
Why another Python tutorial?
----------------------------

What makes this Python tutorial unique is that it has been designed specifically
to meet the needs of, and feedback from, atmospheric and oceanic scientists
making the transition with the NCAR-wide
`pivot-to-Python <https://www.ncl.ucar.edu/Document/Pivot_to_Python/>`_.
In particular, this tutorial should be useful to any scientist who already knows how to program
in some other language but is taking up Python for the first time. By spending the
first course on pure Python without importing any additional packages, our "Your First"
tutorial addresses the concerns that most tutorials either pick up speed too quickly
by going into the intricacies of third-party packages before explaining how Python is
different from other languages, or get too bogged down in basic programming concepts
that anyone with programming experience already knows. This tutorial attempts to hit
the sweet spot between too high-level and too low-level. By using coding examples
with real atmospheric datasets and questions, the skills and techniques taught are
easily applied to actual atmospheric or oceanic workflows.
We hope that this tailored approach to teaching and sharing computational tools
effectively addresses the concerns and needs of the geoscience community.

.. seealso::

   - `Official Python 3 Documentation <https://docs.python.org/3/>`_
   - `Official GitHub Documentation <https://help.github.com/en>`_
   - `Official Git Documentation <https://git-scm.com/doc>`_

..

---------------------------
Requirements & Installation
---------------------------

We will be using the `Conda <https://docs.conda.io/en/latest/>`_ package manager in this tutorial.
If you don't have Conda installed at all,
`please install it. <https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html>`_
Conda is an excellent package manager for Python development, but it is capable of managing
installations of more than just Python packages.  Both Miniconda (just :code:`conda`) and the full
Anaconda (:code:`conda` plus a lot of pre-installed packages and tools) are acceptable,
but we recommend trying to install `Miniconda <https://docs.conda.io/en/latest/miniconda.html>`_
first.  Miniconda is the most lightweight solution, and it is the ideal solution when trying to
install Conda on a remote system (i.e., with only SSH access).

We will also be doing all of the following in a :code:`bash` shell on MacOS.  You may have
different experiences on other OSes, and you may even have problems on MacOS!  That's okay.  If
you have a problem, please `let us know <mailto:xdev@ucar.edu>`_.  We will try to work with you
to find solutions on your OS, and we will post the solution here on this page.

1. Check that you have conda or miniconda installed on your OS by checking your
   conda version:

   .. code-block:: bash

      $ conda --version

   ..

   At the time of writing this, the latest version of conda is 4.8. If you have
   an old version of conda installed, update it.

2. If necessary, update:

   .. code-block:: bash

      $ conda update -n base conda

   ..

   Updating your Conda package manager should not have any effect on your existing
   Conda environments.

   .. note::
      If you have a *really* old version of conda it might be easier to delete it and then reinstall it. But before doing this you have to check your env-list with :bash:`conda env list` to see if there are any environments you created and want to save.

   ..

3. Check your conda version again.

   .. code-block:: bash

      $ conda --version

4. Initialize Conda to work with your shell (.e.g., :code:`bash`):

   .. code-block:: bash

      $ conda init

   This step may modify your shell configuration script (e.g., :code:`.bash_profile`) to
   make the :code:`conda` command available in your shell, and it will make the
   :code:`conda activate` command work.

5. `Install <https://git-scm.com/book/en/v2/Getting-Started-Installing-Git>`_ and `Configure <https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup>`_ Git

   Git is a program that tracks changes made to files. This makes it easy to
   maintain access to multiple versions of your code as you improve it, and
   revert your code back to a previous version if you've made any mistakes.


-------------------------
First Python Script
-------------------------

This section of the tutorial will focus on teaching you Python through the
creation of your first script.  You will learn about syntax and the reasoning
behind why things are done the way they are along the way.  We will also
incorporate lessons on the use of Git because we highly recommend you version
controling your work.

We are assuming you are familiar with bash and terminal commands. If not
`here is a cheat sheet <https://cheatography.com/davechild/cheat-sheets/linux-command-line/>`_.

~~~~~~~~~~~~~~~~~~~
Reading a .txt File
~~~~~~~~~~~~~~~~~~~

In building your first Python script we will set up our workspace, read a
:code:`.txt` file, and learn Git fundamentals.

.. seealso::

   You can watch the `video recording of  Part I <https://drive.google.com/file/d/1PU6UxI1p0kCqQbHmSKuP-ox5rtoxPLtX/view?usp=sharing>`_
   of this tutorial online, and we have a write-up of the `question and answer session following Part I, as well <https://ncar.github.io/xdev/posts/python-tutorial-faq/>`_.

..

Open a terminal to begin.

.. note::

   On Windows, open **Anaconda Prompt**. On a Mac or Linux machine, simply open **Terminal**.

..

1. Create a directory:

   .. code-block:: bash

      $ mkdir python_tutorial

   ..

   The first thing we have to do is create a directory to store our work.
   Let's call it :code:`python_tutorial`.

2. Go into the directory:

   .. code-block:: bash

      $ cd python_tutorial

3. Create a virtual environment for this project:

   .. code-block:: bash

     $ conda create --name python_tutorial python

   ..

   A conda environment is a directory that contains a collection of packages
   or libraries that you would like installed and accessible for this workflow.
   Type :bash:`conda create --name` and the name of your project, here that is
   :code:`python_tutorial`, and then specify that you would like to install Python
   in the virtual environment for this project.

   It is a good idea to create new environments for different projects because
   since Python is open source, new versions of the tools you use may become
   available. This is a way of guaranteeing that your script will use the same
   versions of packages and libraries and should run the same as you expect it
   to.

   .. seealso::

      `More information on Conda environments <https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html>`_

   ..

4. And activate your Conda environment:

   .. code-block:: bash

     $ conda activate python_tutorial

   ..

5. Make the directory a Git repository:

   .. code-block:: bash

      $ git init .

   ..

   A Git repository tracks changes made to files within your project. It looks
   like a :code:`.git/` folder inside that project.

   This command adds version control to this new python_tutorial directory
   and all of its contents.

   .. seealso::

      `More information on Git repositories <https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository>`_

   ..

6. Create a data directory:

   .. code-block:: bash

      $ mkdir data

   ..

   And we'll make a directory for our data.

7. Go into the data directory:

   .. code-block:: bash

      $ cd data

8. Download sample data from the CU Boulder weather station:

   .. code-block:: bash

      $ curl -kO https://sundowner.colorado.edu/weather/atoc8/wxobs20170821.txt

   ..

   This weather station is a Davis Instruments wireless Vantage Pro2 located on
   the CU-Boulder east campus at the SEEC building (40.01 N, 05.24 W, 5250 ft
   elevation). The station is monitored by the Atmospheric and Oceanic Sciences
   (ATOC) department and is part of the larger University of Colorado ATOC
   Weather Network.

9. Check the status of your repository:

   .. code-block:: bash

      $ git status

   ..

   You will see the newly created :bash:`data` directory (which is listed as
   :bash:`./`, since you are currently *in* that directory) is listed as
   "untracked," which means all of the files you added to that directory are
   *also* untracked by Git.  The :bash:`git status` command will tell you what
   to do with untracked files. Those instructions mirror the next 2 steps:

10. Add the file to the Git staging area:

    .. code-block:: bash

       $ git add wxobs20170821.txt

    ..

    By adding this datafile to your directory, you have made a change that is
    not yet reflected in our Git repository. Every file in your working directory is classified
    by git as "untracked", "unmodified", "modified", or "staged."
    Type :bash:`git add` and then the name of the altered file to stage your change,
    i.e. moving a file that is either untracked or modified to the staged category so they can be committed.

    .. seealso::

       `More information on git add <https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository>`_

    ..

11. Check your git status once again:

    .. code-block:: bash

       $ git status

    ..

    Now this file is listed as a "change to be commited," i.e. staged. Staged
    changes can now be commited to your repository history.

12. Commit the file to the Git repository:

    .. code-block:: bash

       $ git commit -m "Adding sample data file"

    ..

    With :bash:`git commit`, you've updated your repository with all the changes
    you staged, in this case just one file.

    .. note::

       On a Windows machine you may see the following: :bash:`warning: LF will be replaced by CRLF.` The file will have its original line endings in your working directory.
       Do not worry too much about this warning. CR refers to "Carriage Return Line Feed" and LF refers to "Line Feed." Both are used to indicate line termination.
       In Windows both a Carriage Return and Line Feed are required to note the end of a line, but in Linux/UNIX only a Line Feed is required. Most text editors can account for line ending differences between opperating systems, but sometimes a conversion is necessary.
       To silence this warning you can type :bash:`git config --global core.autocrlf false` in the terminal.

    ..

13. Look at the Git logs:

    .. code-block:: bash

       $ git log

    ..

    If you type :bash:`git log` you will show a log of all the commits, or changes
    made to your repository.

14. Go back to the top-level directory:

    .. code-block:: bash

       $ cd ..

    ..

15. And now that you've set up our workspace, create a blank Python script,
    called :code:`mysci.py`:

    .. code-block:: bash

       $ touch mysci.py

    ..

    .. note::

       If you are working on a Windows machine it is possible that :bash:`touch` will not be
       recognized as an internal or external command. If this is the case, run
       :bash:`conda install m2-base` to enable unix commands such as :bash:`touch`.

    ..

16. Edit the :code:`mysci.py` file using nano, vim, or your favorite text editor:

    .. code-block:: python
       :linenos:

       print("Hello, world!")

    ..

    Your classic first command will be to print :python:`Hello, world!`.

    .. note::

       On a Windows machine, it is possible `nano` or `vim` are not recognized as text editors within your terminal. In this case simply try to run `mysci.py` to open a notepad editor.

    ..

17. Try testing the script by typing :bash:`python` and then the name of your script:

    .. code-block:: bash

       $ python mysci.py

    ..

    **Yay!** You've just created your first Python script.


18. You probably won't need to run your Hello World script again, so delete the
    :python:`print("Hello, world!")` line and start over with something more useful -
    we'll read the first 4 lines from our datafile.

    Change the :code:`mysci.py` script to read:

    .. code-block:: python
       :linenos:

       # Read the data file
       filename = "data/wxobs20170821.txt"
       datafile = open(filename, 'r')

       print(datafile.readline())
       print(datafile.readline())
       print(datafile.readline())
       print(datafile.readline())

       datafile.close()

    ..

    First create a variable for your datafile name, which is a string - this
    can be in single or double quotes.

    Then create a variable associated with the opened file, here it is called
    :python:`datafile`.

    The :python:`'r'` argument in the open command indicates that we are opening
    the file for reading capabilities. Other input arguments for open include
    :python:`'w'`, for example, if you wanted to write to the file.

    The readline command moves through the open file, always reading the next
    line.

    And remember to close your datafile.

    Comments in Python are indicated with a hash, as you can see in the first
    line :python:`# Read the data file`. Comments are ignored by the interpreter.

    .. seealso::

       `More information on the open() function <https://docs.python.org/3/library/functions.html#open>`_

    ..

19. And test your script again by typing:

    .. code-block:: bash

       $ python mysci.py

    ..

    Testing of your script with :bash:`python mysci.py` should be done every time
    you wish to execute the script. This will no longer be specified as a
    unique step in between every change to our script.

20. Change the :code:`mysci.py` script to read your whole data file:

    .. code-block:: python
       :linenos:

       # Read the data file
       filename = "data/wxobs20170821.txt"
       datafile = open(filename, 'r')

       data = datafile.read()

       datafile.close()

       # DEBUG
       print(data)
       print('data')

    ..

    Our code is similar as before, but now we've read the entire file. To
    test that this worked. We'll :python:`print(data)`. Print statements in python
    require parenthesis around the object you wish to print, in this scenario the data object.

    Try :python:`print('data')` as well. Now Python will print the string
    :code:`data`, as it did for the hello world function, instead of the
    information stored in the variable data.

    Don't forget to execute with :bash:`python mysci.py`.

21. Change the :code:`mysci.py` script to read your whole data file using a context
    manager with:

    .. code-block:: python
       :linenos:

       # Read the data file
       filename = "data/wxobs20170821.txt"
       with open(filename, 'r') as datafile:
          data = datafile.read()

       # DEBUG
       print(data)

    ..

    Again this is a similar method of opening the datafile, but we now use :python:`with open`.
    The :python:`with` statement is a context manager that provides clean-up and
    assures that the file is automatically closed after you've read it.

    The indendation of the line :python:`data = datafile.read()` is very important.
    Python is sensitive to white space and will not work if you mix spaces and
    tabs (Python does not know your tab width). It is best practice to use
    spaces as opposed to tabs (tab width is not consistent between editors).

    Combined these two lines mean: with the datafile opened, I'd like to read
    it.

    And execute with :bash:`python mysci.py`.

    .. seealso::

       `More information on context managers <https://book.pythontips.com/en/latest/context_managers.html>`_

    ..

22. What did we just see? What is the data object? What type is data? How do we
    find out?

    Change the DEBUG section of our script to:

    .. code-block:: python
       :lineno-start: 6

       # DEBUG
       print(type(data))

    ..

    And execute with :bash:`python mysci.py`

    Object types refer to :python:`float`, :python:`integer`, :python:`string`
    or other types that you can create.

    Python is a dynamically typed language, which means you don't have to
    explicitly specify the datatype when you name a variable, Python will
    automatically figure it out by the nature of the data.

23. Now, clean up the script by removing the DEBUG section, before we commit
    this to Git.

24. Let's check the status of our Git repository

    .. code-block:: bash

       $ git status

    ..

    .. note::

       Take a look at which files have been changed in the repository!

    ..

25. Stage these changes:

    .. code-block:: bash

       $ git add mysci.py

    ..

26. Let's check the status of our Git repository,again. What's different from
    the last time we checked the status?

    .. code-block:: bash

       $ git status

    ..

27. Commit these changes:

    .. code-block:: bash

       $ git commit -m "Adding script file"

    ..

    Here a good commit message :code:`-m` for our changes would be
    :code:`"Adding script file"`

28. Let's check the status of our Git repository, now. It should tell you that
    there are no changes made to your repository (i.e., your repository is
    up-to-date with the state of the code in your directory).

    .. code-block:: bash

       $ git status

    ..

29. Look at the Git logs, again:

    .. code-block:: bash

       $ git log

    ..

    You can also print simplified logs with the :code:`--oneline` option.

-----

That concludes the first lesson of this virtual tutorial.

In this section you set up a workspace by creating your directory, conda
environment, and git repository. You downloaded a .txt file and read it using
the Python commands of :python:`open()`, :python:`readline()`, :python:`read()`,
:python:`close()`, and :python:`print()`, as well as the context manager
:python:`with`. You should be familiar with the :python:`str` datatype. You
also used fundamental git commands such as :bash:`git init`, :bash:`git status`,
:bash:`git add`, :bash:`git commit`, and :bash:`git log`.


.. seealso::

   - `Conda environments <https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html>`_
   - `Git repositories <https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository>`_
   - `The open() function <https://docs.python.org/3/library/functions.html#open>`_
   - `Context managers <https://book.pythontips.com/en/latest/context_managers.html>`_

..


~~~~~~~~~~~~~~~~~~~~~~~~~~
Creating a Data Dictionary
~~~~~~~~~~~~~~~~~~~~~~~~~~

This is intended to pick off right where "Reading in a .txt File" left off - you
had just commited your new script file that reads in the data from a file as a string.
You will now manipulate your data into a more usable format - a dictionary.
In doing so you will learn how to write iterative for loops and about Python
data structures.

.. seealso::

   You can watch a video recording of `Part II <https://drive.google.com/file/d/1DwXaLQH28aqqR1NwOLEYzbR86zQNlTVk/view?usp=sharing>`_
   of this tutorial online, and we have a write-up of the `question and answer session following Part II, as well <https://ncar.github.io/xdev/posts/python-tutorial-faq-part-2/>`_.

..

Let's begin.

1. One big string isn't very useful, so use :python:`str.split()` to parse the data
   file into a data structure you can use.

   Change the :code:`mysci.py` script to read:

   .. code-block:: python
      :linenos:

      # Initialize my data variable
      data = []

      # Read and parse the data file
      filename = "data/wxobs20170821.txt"
      with open(filename, 'r') as datafile:

       # Read the first three lines (header)
       for _ in range(3):
          datafile.readline()

       # Read and parse the rest of the file
       for line in datafile:
          datum = line.split()
          data.append(datum)

      # DEBUG
      for datum in data:
         print(datum)

   ..

   The first thing that is different in this script is an initialized data
   variable; :python:`data = []` creates the variable data as an empty :code:`list` which we
   will populate as we read the file. Python :code:`list` objects are a collection data type
   that contain ordered and changeable - meaning you can call information out of
   the :code:`list` by its index and you can add or delete elements to your :code:`list`. Lists
   are denoted by square brackets, :python:`[]`.

   Then with the datafile open for reading capabilities, we are going to write
   two separate :python:`for` loops. A :python:`for` loop is used for iterating
   over a sequence (such as a list). It is important to note the syntax of Python
   :python:`for` loops: the :python:`:` at the end of the :python:`for` line, the
   tab-indentation of all lines within the :python:`for` loop, and perhaps the
   absence of an :code:`end for` that is found in languages such as Matlab.

   In your first :python:`for` loop, loop through the dummy variable :python:`_`
   in :python:`range(3)`. The :python:`range` function returns a sequence of
   numbers, starting at 0 and incrementing by 1 (by default), ending at the
   specified length. Here if you were to :python:`print(_)` on each line of the
   for loop you would see:

   .. code-block:: python

      0
      1
      2

   ..

   Try it out if you are unsure of how this works. Here the :python:`_` variable
   is a placeholder, meaning the variable is never called within the loop.

   So again, in the first :python:`for` loop, you execute the :python:`readline`
   command (which you will remember moves down to the next line each time it is
   consecutively called) 3 times to read through the file header (which is 3
   lines long). **Yay!** You have just written your first :python:`for` loop!

   Then in a second :python:`for` loop, you loop through lines in the remainder of
   your datafile. On each line, split it along white space. The
   :python:`string.split()` method splits a string into a list on a specified
   separator, the default being white space. You could use any character you
   like, but other useful options are :python:`/t` for splitting along tabs or
   :python:`,` along commas.

   Then you :python:`append` this split line list to the end of your data :python:`list`.
   The :python:`list.append()` method adds a single item to the end of your :python:`list`.
   After every line in your :python:`for` loop iteration, the data :python:`list` that was
   empty is one element longer. Now we have a :python:`list` of :python:`list`\s for our
   data variable - a :python:`list` of the data in each line for multiple lines.

   When you print each datum in data, you'll see that each datum is a :python:`list`
   of :python:`string` values.

   We just covered a lot of Python nuances in a very little bit a code!

   .. seealso::

      `More information on for-loops <https://book.pythontips.com/en/latest/for_-_else.html>`_
      `More information on Python lists <https://docs.python.org/3/tutorial/datastructures.html#more-on-lists>`_

   ..

2. Now, to practice list indexing, get the first, 10th, and last row in data.

   Change the DEBUG section of our :code:`mysci.py` script to:

   .. code-block:: python
      :lineno-start: 17

      # DEBUG
      print(data[0])
      print(data[9])
      print(data[-1])

   ..

   Index your list by adding the number of your index in square brackets,
   :python:`[]`, after the name of the :python:`list`. Python is 0-indexed so
   :python:`data[0]` refers to the first index and :python:`[-1]` refers to
   the last index.

3. Now, to practice slice indexing, get the first 10 rows in data.

   Change the DEBUG section of our :code:`mysci.py` script to:

   .. code-block:: python
      :lineno-start: 17

      # DEBUG
      for datum in data[0:10]:
         print(datum)

   ..

   Using a colon, :python:`:`, between two index integers :python:`a` and
   :python:`b`, you get all indexes between :python:`a` and :python:`b`. See
   what happens when you print :python:`data[:10]`, :python:`data[0:10:2]`, and
   :python:`data[slice(0,10,2)]`.  What's the difference?

4. Now, to practice nested indexing, get the 5th, the first 5, and every other
   column of row 9 in the data object.

   Change the DEBUG section of the :code:`mysci.py` script to:

   .. code-block:: python
      :lineno-start: 17

      # DEBUG
      print(data[8][4])
      print(data[8][:5])
      print(data[8][::2])

   ..

   In nested :python:`list` indexing, the first index determines the row, and the
   second determines the element from that row. Also try printing
   :python:`data[5:8][4]`, why doesn't this work?

5. Clean up the file (remove DEBUG section), stage the changes, and commit.

   .. code-block:: bash

      $ git add mysci.py
      $ git commit -m "Parsing file"

   ..


6. Can you remember which column is which? Is time the first column or the
   second? Which column is the temperature?

   Each column is a time-series of data. We would ideally like each time-series
   easily accessible, which is not the case when data is row-column ordered
   (like it currently is). (Remember what happens when you try to do something
   like :python:`data[:][4]`!)

   Let's get our data into a more convenient named-column format.

   Change :code:`mysci.py` to the following:

   .. code-block:: python
      :linenos:

      # Initialize my data variable
      data = {'date': [],
        'time': [],
        'tempout': []}

      # Read and parse the data file
      filename = "data/wxobs20170821.txt"
      with open(filename, 'r') as datafile:

         # Read the first three lines (header)
         for _ in range(3):
            datafile.readline()

         # Read and parse the rest of the file
         for line in datafile:
            split_line = line.split()
            data['date'].append(split_line[0])
            data['time'].append(split_line[1])
            data['tempout'].append(split_line[2])

      # DEBUG
      print(data['time'])

   ..

   First we'll initialize a dictionary, :python:`dict`, indicated by the curly
   brackets, :python:`{}`. Dictionaries, like :python:`list`\s, are changeable, but they
   are unordered. They have keys, rather than positions, to point to their
   elements. Here you have created 3 elements of your dictionary, all currently
   empty :python:`list`\s, and specified by the keys :python:`date`, :python:`time`, and
   :python:`tempout`. Keys act similarly to indexes: to pull out the :python:`tempout`
   element from data you would type :python:`data['tempout']`.

   Grab date (the first column of each line), time (the second column of each
   line), and temperature data (the third column), from each line and
   :python:`append` it to the :python:`list` associated with each of these data variables.

   .. seealso::

      `More on Python dictionaries <https://docs.python.org/3/tutorial/datastructures.html#dictionaries>`_

   ..

7. Clean up (remove DEBUG section), stage, and commit

   .. code-block:: bash

      $ git add mysci.py
      $ git commit -m "Parsing select time-series"

   ..

8. Now it's easy to get the time-series information for each column that we are
   interested in grabbing, and we can get each column by name. However,
   everything read from the text file is a :python:`str`. What if we want to do math on
   this data, then we need it to be a different data type!

   So, let's convert the tempout time-series to be a :python:`float` by changing the
   line:

   .. code-block:: python
      :lineno-start: 19

      data['tempout'].append(split_line[2])

   ..

   to:

   .. code-block:: python
      :lineno-start: 19

      data['tempout'].append(float(split_line[2]))

   ..

   The :python:`float` datatype refers to floating point real values - the datatype
   of any numbers with values after a decimal point. You could also change the
   datatype to :python:`int`, which will round the values down to the closest full
   integer.

   .. seealso::

      `More on Python numeric types (int, float, complex) <https://docs.python.org/3/library/stdtypes.html#numeric-types-int-float-complex>`_

   ..

9. Add a DEBUG section at the end and see what :python:`data['tempout']` now looks
   like.

   Do you see a difference? It should now be a list of floats.

10. Clean up (remove DEBUG section), stage, and commit

    .. code-block:: bash

       $ git add mysci.py
       $ git commit -m "Converting tempout to floats"

    ..

11. This seems great, so far! But what if you want to read more columns to our
    data later? You would have to change the initialization of the data
    variable (at the top of :code:`mysci.py`\) and have to add the appropriate line
    in the "read and parse" section. Essentially, that means you need to
    maintain 2 parts of the code and make sure that both remain consistent with
    each other.

    This is generally not good practice. Ideally, you want to be able to change
    only one part of the code and know that the rest of the code will remain
    consistent. So, let's fix this.

    Change :code:`mysci.py` to:

    .. code-block:: python
       :linenos:

       # Column names and column indices to read
       columns = {'date': 0, 'time': 1, 'tempout': 2}

       # Data types for each column (only if non-string)
       types = {'tempout': float}

       # Initialize my data variable
       data = {}
       for column in columns:
          data[column] = []

       # Read and parse the data file
       filename = "data/wxobs20170821.txt"
       with open(filename, 'r') as datafile:

          # Read the first three lines (header)
          for _ in range(3):
             datafile.readline()

          # Read and parse the rest of the file
          for line in datafile:
             split_line = line.split()
             for column in columns:
                i = columns[column]
                t = types.get(column, str)
                value = t(split_line[i])
                data[column].append(value)

       # DEBUG
       print(data['tempout'])

    ..

    You have now created a columns :python:`dict` that points each data variable to
    its column-index. And a types :python:`dict`, that indicates what type to convert
    the data when necessary. When you want new variables pulled out of the
    datafile, change these two variables.

    Initializing the data :python:`dict` now includes a :python:`for` loop, where for each
    variable specified in columns, that key is initialized pointing to an empty
    :python:`list`. This is the first time you have looped over a :python:`dict` and added
    key-value pairs to a :python:`dict` via assignment.

    When reading and parsing the file, you created your first nested :python:`for`
    loop. For every line of the datafile, split that line - and then for every
    desired variable in the columns :python:`dict` (date, time, tempout): grab the
    datum from the current split line with the specified index (0, 1, 2), use
    the :python:`dict.get()` method to find the desired datatype if specified
    (avoiding :python:`key-not-found` errors and defaulting to :python:`str` if
    unspecified), convert the datum to the desired datatype, and :python:`append`
    the datum to the :python:`list` associated with each column key within the data
    :python:`dict`.

12. Clean up (remove DEBUG section), stage, and commit

    .. code-block:: bash

       $ git add mysci.py
       $ git commit -m "Refactoring data parsing code"

    ..

-----

That concludes the second lesson of this virtual tutorial.

In this section you saved the variables of date, time, and tempout in a data
dictionary.

You should now be familiar with the data structures :python:`list`\s (as well as list
indexing, nested lists, and the command :python:`list.append()`), :python:`dict`\s (their
keys and the command :python:`dict.get()`), and :python:`range`\s. You also learned to write
:python:`for` loops, about the :python:`float` datatype, and using the Python commands
:python:`str.split()`.

.. seealso::

   - `For-loops <https://book.pythontips.com/en/latest/for_-_else.html>`_
   - `Lists <https://docs.python.org/3/tutorial/datastructures.html#more-on-lists>`_
   - `Dictionaries <https://docs.python.org/3/tutorial/datastructures.html#dictionaries>`_

..


~~~~~~~~~~~~~~~~~
Writing Functions
~~~~~~~~~~~~~~~~~

This is intended to pick off right where "Creating a Data Dictionary" left off - you
had just commited your new script that reads the file, saving the variables of date,
time, and tempout in a data dictionary.
In this section you will compute wind chill index by writing your first
function and learning about basic math operators.

.. seealso::

   You can watch a video recording of `Part III <https://drive.google.com/file/d/1eyPn_GXmvKlWe-e7p97HxS4bRbsTbvyI/view?usp=sharing>`_
   of this tutorial online, and we have a write-up of the `question and answer session following Part III, as well <https://ncar.github.io/xdev/posts/python-tutorial-faq-part-3/>`_.

..

Let's begin.

1. Okay, now that you've read the data in a way that is easy to modify later,
   it is time to actually do something with the data.

   Compute the wind chill factor, which is the cooling effect of the wind. As
   wind speed increases the rate at which a body loses heat increases. The
   formula for this is:

   .. math::

      WCI = a + (b * t) - (c * v^{0.16}) + (d * t * v^{0.16})

   ..

   Where *WCI* refers to the Wind Chill in degrees F, *t* is temperature in
   degrees F, *v* is wind speed in mph, and the other variables are as
   follows: *a* = 35.74, *b* = 0.6215, *c* = 35.75, and *d* = 0.4275.
   Wind Chill Index is only defined for temperatures within the range -45 to
   +45 degrees F.

   You've read the temperature data into the tempout variable, but to do this
   calculation, you also need to read the windspeed variable from column 7.

   Modify the columns variable to read:

   .. code-block:: python
      :linenos:

      # Column names and column indices to read
      columns = {'date': 0, 'time': 1, 'tempout': 2, 'windspeed': 7}

   ..

   and modify the types variable to be:

   .. code-block:: python
      :lineno-start: 4

      # Data types for each column (only if non-string)
      types = {'tempout': float, 'windspeed': float}

   ..


2. Great! Save this in your Git repo. Stage and commit

   .. code-block:: bash

      $ git add mysci.py
      $ git commit -m "Reading windspeed as well"

   ..

3. Now, let's write our first function to compute the wind chill factor. We'll
   add this function to the bottom of the file.

   .. code-block:: python
      :lineno-start: 29

      # Compute the wind chill temperature
      def compute_windchill(t, v):
         a = 35.74
         b = 0.6215
         c = 35.75
         d = 0.4275

         v2 = v ** 2
         wci = a + (b * t) - (c * v2) + (d * t * v2)
         return wci

   ..

   To indicate a function in python you type :python:`def` for define, the name of your
   function, and then in parenthesis the input arguments of that function,
   followed by a colon. The preceding lines,the code of your function, are all tab-indented.
   If necessary specify your return value.

   .. seealso::

      `More on user defined functions <https://docs.python.org/3/reference/compound_stmts.html#function-definitions>`_

   ..

   Here is your first introduction to math operators in Python. Addition,
   subtraction, and multiplication look much like you'd expect. A double
   astericks, :python:`**`, indicates an exponential. A backslash, :python:`/`,
   is for division, and a double backslash, :python:`//`, is for integer division.

   And then let's compute a new list with windchill data at the bottom of
   :code:`mysci.py`\:

   .. code-block:: python
      :lineno-start: 40

      # Compute the wind chill factor
      windchill = []
      for temp, windspeed in zip(data['tempout'], data['windspeed']):
         windchill.append(compute_windchill(temp, windspeed))

   ..

   Now we'll call our function. Initialize a :python:`list` for wind chill with empty
   square brackets, :python:`[]`. And in a :python:`for` loop, loop through our temperature
   and wind speed data, applying the function to each :python:`tuple` data pair.
   :python:`tuple`\s are ordered like :python:`list`\s, but they are indicated by
   parenthesis, :python:`()`, instead of square brackets and cannot be changed or
   appended. :python:`tuple`\s are generally faster than :python:`list`\s.

   We use the :python:`zip` function in Python to automatically unravel the
   :python:`tuple`\s. Take a look at :python:`zip([1,2], [3,4,5])`. What is the result?

   And finally, add a DEBUG section to see the results:

   .. code-block:: python
      :lineno-start: 45

      # DEBUG
      print(windchill)

   ..

4. Clean up, stage, and commit


   .. code-block:: bash

      $ git add mysci.py
      $ git commit -m "Compute wind chill factor"

   ..

5. Now, the wind chill factor is actually in the datafile, so we can read it
   from the file and compare that value to our computed values. To do this, we
   need to read the windchill from column 12 as a :python:`float`:

   Edit the columns and types :python:`dict`:

   .. code-block:: python
      :linenos:

      # Column names and column indices to read
      columns = {'date': 0, 'time': 1, 'tempout': 2, 'windspeed': 7,
                 'windchill': 12}

   ..

   ..

   .. note::

      Python requires that you indent any continued lines.  Take note that we indented the continued line above to align it with the starting :python:`{`-symbol.

   and

   .. code-block:: python
      :lineno-start: 5

      # Data types for each column (only if non-string)
      types = {'tempout': float, 'windspeed': float, 'windchill': float}

   ..

   Then, in a DEBUG section at the end of your script, compare the two
   different values (one from data and one computed by our function):

   .. code-block:: python
      :lineno-start: 46

      # DEBUG
      for wc_data, wc_comp in zip(data['windchill'], windchill):
         print(f'{wc_data:.5f}   {wc_comp:.5f}   {wc_data - wc_comp:.5f}')

   ..

   Using a :python:`f-string` with float formatting you can determine the precision
   to which to print the values. The :python:`.5f` means you want 5 places after the
   decimal point.

   .. seealso::

      `More on string formatting <https://docs.python.org/3/library/string.html#format-string-syntax>`_

   ..

   Test the results. What do you see? Our computation isn't very good is it?

6. Clean up, stage, and commit

   .. code-block:: bash

      $ git add mysci.py
      $ git commit -m "Compare wind chill factors"

   ..

7. Now, format the output so that it's easy to understand and rename this
   script to something indicative of what it actually does.

   To the end of the file, add:

   .. code-block:: python
      :lineno-start: 46

      # Output comparison of data
      print('                ORIGINAL  COMPUTED')
      print(' DATE    TIME  WINDCHILL WINDCHILL DIFFERENCE')
      print('------- ------ --------- --------- ----------')
      zip_data = zip(data['date'], data['time'], data['windchill'], windchill)
      for date, time, wc_orig, wc_comp in zip_data:
         wc_diff = wc_orig - wc_comp
         print(f'{date} {time:>6} {wc_orig:9.6f} {wc_comp:9.6f} {wc_diff:10.6f}')

   ..

   Here you used *f-*:python:`string` formatting with more *f-*:python:`string` formatting
   options. The :python:`>6` indicates that you'd like the characters of the string to be
   right-justified and to take up 6 spaces.

   The :python:`9f` specifies that you want the value to fill 9 spaces, so :python:`9.6f`
   indicates you'd like the value to fill 9 spaces with 6 of them being after
   the decimal point. Same concept for :python:`10.6f`.

   You now have your first complete Python script!

8. DON'T CLEAN UP! Just stage and commit

   .. code-block:: bash

      $ git add mysci.py
      $ git commit -m "Output formatting comparison data"

   ..

9. Let's rename this script to something meaningful and indicative of the
   computation inside.

   .. code-block:: bash

      $ git mv mysci.py windchillcomp.py
      $ git commit -m "Renaming first script"

   ..

10. Let's push to GitHub!

    1. First you have to create a remote repository. Go to `GitHub <https://github.com/>`_
       and create or login to your account.

    2. At the top right of any Github page, there is a '+' icon. Click that,
       then select 'New Repository'.

    3. Name your repository :code:`python_tutorial`\.
       It is best practice for your local project and GitHub repository to
       share a name.

    4. And click "Create Repository"

    5. Copy the link to your GitHub repository.

       Copy the link in the input right beneath the title, it should look
       something like this:

       :code:`https://github.com/<user_name>/<repo>.git`

    6. Then to set your remote repository, in your project terminal type:

       .. code-block:: bash

          $ git remote add origin <remote repository URL>

       ..

       .. note::

          Your remote repository URL is the link you copied in step 5!

       ..

    7. And verify your remote repository:

       .. code-block:: bash

          $ git remote -v

       ..

    8. And finally push your project to GitHub:

       .. code-block:: bash

          $ git push origin master

       ..

    Think of GitHub as online storage for versions of your project, much like
    hosting your code in a Google Drive, but with better features specific to
    coding. A lot of GitHub's features show their usefulness when you are
    working collaboratively, sharing your code with other scientists, or if
    you wanted to display and easily visualize changes in your code between
    commits.

-----

That concludes the "First Python Script" virtual tutorial where you learned to
write your first Python script.

In this section you calculated wind chill index by writing and calling your
first function. You also learned about Python math operators, the :python:`zip()`
command, :python:`tuple` datastructure, *f-*:python:`string` formatting, and how to push your
repository to GitHub.

.. seealso::

   - `User defined functions <https://docs.python.org/3/reference/compound_stmts.html#function-definitions>`_
   - `String formatting <https://docs.python.org/3/library/string.html#format-string-syntax>`_

..


-----------------------------
First Python Package
-----------------------------

In this section of the tutorial we will learn how to create a Python package 
and the basics of how to use built-in package :code:`math`\. This will prepare you 
to learn any package you think may be useful for your scientific analysis.

~~~~~~~~~~~~~~~~~~~~~~~~~~
Creating Your Own Package
~~~~~~~~~~~~~~~~~~~~~~~~~~

In this section you will learn how to move functions and code blocks into 
Python packages that you can import into your analysis 
methods, making them easier to write, read, and share. 

Perhaps you are already familiar with importing packages into 
your workflow. Many scientists pass around files that contain 
unique user-written functions to reduce redundant work between 
scientists, but what if the original author found a bug in their 
script? It is difficult to track down every user of their code to let them know. 
In Python, package managers help you know what 
version of those functions you are using. Matlab also has packages 
that you can pay extra money to install and use - again Python 
is free! 

Open a terminal to begin and make sure you are in the 
:code:`python_tutorial` directory and have activated the corresponding environment.

1. Make a copy of your first script with a new name:
   
   .. code-block:: bash

      $ cp windchillcomp.py heatindexcomp.py
   
   ..

2. Git add and commit this new file:

   .. code-block:: bash

      $ git add heatindexcomp.py
      $ git commit -m "Copying first script to start second"

   ..

3. Now you will compute the Heat Index.

   Like wind chill, which is a measure of how much 
   colder the weather feels to the human body due 
   to wind speed, heat index is a measure of how 
   much hotter the weather feels to the human body 
   due to humidity. The Rothfusz formula for heat 
   index is:

   .. math::

      \textit{HI} = a + (b * T) + (c * H) + (d * T * H) + (e * T^2) + (f * H^2) + (g * T^2 * H) + (h * T * H^2) + (i * T^2 * H^2)

   ..

   where *HI* is the Heat Index, *T* is temperature is in degrees F, 
   *H* is humidity in %, *a* = -42.379, *b* = 2.04901523, 
   *c* = 10.14333127, *d* = 0.22475541, *e* = 0.00683783, 
   *f* = 0.05481717, *g* = 0.00122874, *h* = 0.00085282, and 
   *i* = 0.00000199. The Roothfusz regression is not valid for 
   extreme temperature or humidity conditions.

   Replace the :code:`compute_windchill` function with in your :code:`heatindexcomp.py` script with
   a :code:`compute_heatindex` function:
   
   .. code-block:: python
      :lineno-start: 30
         
      # Compute the heat index
      def compute_heatindex(t, hum):
         a = -42.379
         b = 2.04901523
         c = 10.14333127
         d = 0.22475541
         e = 0.00683783
         f = 0.05481717
         g = 0.00122874
         h = 0.00085282
         i = 0.00000199

         rh = hum / 100

         hi = a + (b * t) + (c * rh) + (d * t * rh) 
            + (e * t**2) + (f * rh**2) + (g * t**2 * rh) 
            + (h * t * rh**2) + (i * t**2 * rh**2)
         return hi

   ..
   
4. Change the :code:`columns` and :code:`types` dictionary we read from the data file to 
   read in the humidity and heat index values as :code:`float`\s:
   
   .. code-block:: python
      :lineno-start: 1

      # Column names and column indices to read
      columns = {'date': 0, 'time': 1, 'tempout': 2, 'humout': 5, 'heatindex': 13}
   
      # Data types for each column (only if non-string)
      types = {'tempout': float, 'humout': float, 'heatindex': float}
   
   ..

5. Update the function call and printing sections of the script to match:
   
   .. code-block:: python
      :lineno-start: 49

      # Compute the heat index
      heatindex = []
      for temp, hum in zip(data['tempout'], data['humout']):
         heatindex.append(compute_heatindex(temp, hum))

      # Output comparison of data
      print('                ORIGINAL  COMPUTED')
      print(' DATE    TIME  HEAT INDX HEAT INDX DIFFERENCE')
      print('------- ------ --------- --------- ----------')
      for date, time, hi_orig, hi_comp in zip(data['date'], data['time'], data['heatindex'], heatindex):
         print(f'{date} {time:>6} {hi_orig:9.6f} {hi_comp:9.6f} {hi_orig-hi_comp:10.6f}')
   
   ..
   
   Run this script with \":code:`python heatindexcomp.py`\" and see the results. 

   So far you have only revisited concepts from "Your First Script".

6. Git stage and commit this new script.

   .. code-block:: bash

      $ git add heatindexcomp.py
      $ git commit -m "Updating new heat index script"

   ..

7. Now, you have two scripts that do very 
   similar things. In fact, all of the data reading 
   and parsing code is duplicated! And the output is 
   similarly formatted, too.  Let's remove that duplication!
   
   Create a new file called :code:`readdata.py`\:

   .. code-block:: bash

      $ touch readdata.py

   ..
   
   This new file will include the common code for reading the data file from both the 
   :code:`windchillcomp.py` and :code:`heatindexcomp.py` scripts.

8. Copy and paste the lines for reading in the data file into :code:`readdata.py`\:

   .. code-block:: python
      :lineno-start: 1

      # Initialize my data variable
      data = {}
      for column in columns:
         data[column] = []

      # Read and parse the data file
      with open(filename, 'r') as datafile:

         # Read the first three lines (header)
         for _ in range(3):
            datafile.readline()

         # Read and parse the rest of the file
         for line in datafile:
            split_line = line.split()
            for column in columns:
               i = columns[column]
               t = types.get(column, str)
               value = t(split_line[i])
               data[column].append(value)

   ..

9. Turn these lines into a function:

   .. code-block:: python
      :lineno-start: 1
         
      def read_data(columns, types={}, filename="data/wxobs20170821.txt"):
         # Initialize my data variable
         data = {}
         for column in columns:
            data[column] = []

         # Read and parse the data file
         with open(filename, 'r') as datafile:

            # Read the first three lines (header)
            for _ in range(3):
               datafile.readline()

            # Read and parse the rest of the file
            for line in datafile:
               split_line = line.split()
               for column in columns:
                  i = columns[column]
                  t = types.get(column, str)
                  value = t(split_line[i])
                  data[column].append(value)

   ..

   The function arguments for our :code:`read_data` function are :code:`columns`\, :code:`types`\, and :code:`filename`\.
   The :code:`types` and :code:`filename` variables are both keyword arguments, which means that it is not
   necessary to include them in your function call; if you do not call them, their value is taken as what they are
   assigned to in the function definition. 
      
   When you see :code:`types={}` it means that :code:`types` is presumed to be an empty dictionary when unspecified 
   (and so you don't have to specify it every time you call the function when this keyword isn't relevant). 
    
   Similarly, :code:`filename` is set to the path of our data file as long as the user doesn't specify a different 
   file. 
      
   Keyword arguments can be called in any order, but they must follow all *positional* arguments
   (i.e., arguments that do not have default values).

10. Add a docstring to the function:

    .. code-block:: python
       :lineno-start: 1
         
       def read_data(columns, types={}, filename="data/wxobs20170821.txt"):
          """
          Read data from CU Boulder Weather Station data file
       
          Parameters:
             columns: A dictionary of column names mapping to column indices
             types: A dictionary of column names mapping to types to which
                to convert each column of data
             filename: The string path pointing to the CU Boulder Weather
                   Station data file
          """

          # Initialize my data variable
          data = {}
          for column in columns:
             data[column] = []

          # Read and parse the data file
          with open(filename, 'r') as datafile:

             # Read the first three lines (header)
             for _ in range(3):
                datafile.readline()

             # Read and parse the rest of the file
             for line in datafile:
                split_line = line.split()
                for column in columns:
                   i = columns[column]
                   t = types.get(column, str)
                   value = t(split_line[i])
                   data[column].append(value)

    ..

    The section between the tripple quotes :code:`"""` is the docstring. 
    The "Read data from CU Boulder 
    Weather Station data file . . ." describing the utility 
    of the function and the list of parameters are 
    standard information included in a docstring, but there is no requirement.  Everything
    between the triple quotes is essentially a comment that you can write and format any
    way you want.  

    This new file is a *module*. Modules are simply 
    files containing Python code, meant to be called 
    up (or "imported") within a different Python script.  We'll get to this later.

11. Stage and commit this new file:

    .. code-block:: bash

       $ git add readdata.py
       $ git commit -m "Adding new readdata module"

    ..

12. Amend your two Python (:code:`heatindexcomp.py` and :code:`windchillcomp.py`) scripts by deleting the equivalent read-file code in them.

13. Add the following import statement to the top of each script:

    .. code-block:: python
       :lineno-start: 1

       from readdata import read_data 

    ..

    In python you can call up functionality from scripts outside of your active script using the 
    :code:`import` statement. Here we import our :code:`read_data` function from the :code:`readdata` module. 
    And now we can call up the function from these scripts.
   
14. And after the initializations of the :code:`columns` and :code:`types` variables, replace the 
    deleted code with a function call:

    .. code-block:: python
       :lineno-start: 9
  
       # Read data from file
       data = read_data(columns, types=types)   

    ..
    
    The :code:`types=types` says that the input argument :code:`types` is being set equal to our dictionary :code:`types`.
   
    Test out both of these scripts to make sure they still work!

15. Do a \":code:`git status`\" now.  

    Do you notice something new?  Running our new scripts created the `__pycache__` directory.  

    What is :code:`__pycache__`\?
    When you run a python program with an :code:`import` 
    command, Python learns that you have written code 
    that you may call again. The interpreter compiles 
    your scripts to bytecode and stores them in a cache, 
    making your scripts run a little faster next time. 
    As a user can for the most part ignore this new folder. 
    If you change or delete your scripts they will be 
    recompiled and reappear in this folder.

    However, you *don't* want to add this directory to 
    our project repository, so before you commit 
    anything, tell git to ignore it!

    Create a new file (in the top-level directory 
    of your project) called :code:`.gitignore` 

    .. code-block:: bash

       $ touch .gitignore

    ..

    with the following contents:

    .. code-block:: bash

       __pycache__/

    ..

16. Do another :code:`git status`\.  What do you see?

    Now, instead of :code:`__pycache__` being listed as 
    "untracked", you see :code:`.gitignore` being listed as 
    "untracked", and no mention of :code:`__pycache__`\.

17. Stage and commit the new :code:`.gitignore` file.

    .. code-block:: bash

       $ git add .gitignore
       $ git commit -m "Ignoring pycache"

    ..

    Do another :code:`git status`.  Notice that
    the edits you made to your two scripts have still 
    not been committed to the project repository!  
    Because they have not yet been staged.

18. Stage *both files* and commit all new changes in one commit:

    .. code-block:: bash

       $ git add -a
       $ git commit -m "Refactor scripts to use new module"

    ..

    You can type :code:`-a` instead of the name of your files to add all unstaged changes.

19. There is still have some duplicated 
    code between the two scripts. Let's combine the final 
    output code and printing code.

    Create another module file called :code:`printing.py`\:

    .. code-block:: bash

       $ touch printing.py

    ..

    And create a printing function (with docstring!) in :code:`printing.py`\:

    .. code-block:: python
       :lineno-start: 1

       def print_comparison(name, date, time, original_data, computed_data):
          """
          Print a comparison of two timeseries (original and computed)

          Parameters:
             name: A string name for the data being compared. (Limited
                to 9 characters in length)
             date: List of strings representing the dates for each data element
             time: List of strings representing time of day for each data element
             original_data: List of original data (floats)
             computed_data: List of computed data (floats)
          """

          print(f'                ORIGINAL  COMPUTED')
          print(f' DATE    TIME  {name.upper():>9} {name.upper():>9} DIFFERENCE')
          print(f'------- ------ --------- --------- ----------')
          for date, time, orig, comp in zip(date, time, original_data, computed_data):
             print(f'{date} {time:>6} {orig:9.6f} {comp:9.6f} {orig-comp:10.6f}')
    ..

    The only new functionality shown here is 
    :code:`string.upper()` (or, specifically, :code:`name.upper()`\), which capitalizes all lower case 
    letters in a string.

20. Edit the two scripts to use this new module (similar methods to step #12-14), and test your results.

    Try to do this on your own first, but if you are getting error messages the solution looks like:

    1)  Add the \":code:`from printing import print_comparison`\" line to the top of each script.

    2) Replace the printing output section at the bottom of each script with:

       .. code-block:: python
          :lineno-start: 29

          # Output comparison of data
          print_comparison('WINDCHILL', data['date'], data['time'], data['windchill'], windchill)

       ..

       or

       .. code-block:: python
          :lineno-start: 37

          # Output comparison of data
          print_comparison('HEAT INDX', data['date'], data['time'], data['heatindex'], heatindex)

       ..

21. Stage all changes and commit:

    .. code-block:: bash
   
       $ git add -a
       $ git commit -m "Creating printing module"

    ..

22. You now have 2 different modules related 
    to the same project.  It is best practice
    to separate different functions into different 
    modules depending upon the kind of functionality 
    they represent.  In this case, you've separated 
    out the concepts of "data input" and "printing 
    output" into different modules.

    Do the same thing with the computation functions, 
    :code:`compute_windchill` and :code:`compute_heatindex`\.

    Move these functions into a new module called 
    :code:`computation.py`\, and modify the scripts to use 
    this new module.  Remember to add docstrings!

    Try to do this on your own first!!

    Your new :code:`computation.py` module should look 
    similar to the following:

    .. code-block:: python
       :lineno-start: 1

       def compute_windchill(t, v):
          """
          Compute the wind chill factor given the temperature and wind speed

          NOTE: This computation is valid only for 
             temperatures between -45F and +45F and for 
             wind speeds between 3 mph and 60 mph.

          Parameters:
             t: The temperature in units of F
             v: The wind speed in units of mph
          """

          a = 35.74
          b = 0.6215
          c = 35.75
          d = 0.4275

          v16 = v ** 0.16
          wci = a + (b * t) - (c * v16) + (d * t * v16)
          return wci


       def compute_heatindex(t, hum):
          """
          Compute the heat index given the temperature and the humidity

          Parameters:
             t: The temperature in units of F
             hum: The relative humididy in units of %
          """

          a = -42.379
          b = 2.04901523
          c = 10.14333127
          d = 0.22475541
          e = 0.00683783
          f = 0.05481717
          g = 0.00122874
          h = 0.00085282
          i = 0.00000199

          rh = hum / 100

          hi = a + (b * t) + (c * rh) + (d * t * rh) 
          + (e * t**2) + (f * rh**2) + (g * t**2 * rh) 
          + (h * t * rh**2) + (i * t**2 * rh**2)
          return hi
    ..

    And then modified the scripts accordingly as in steps #12-14 and #18
    by adding your import statements \":code:`from computation import compute_windchill`\"
    OR \":code:`from computation import compute_heatindex`\" and
    removing the redundant function definitions.

    Your two scripts should look as follows:

    For :code:`windchillcomp.py`\:

    .. code-block:: python
       :lineno-start: 1

       from readdata import read_data
       from printing import print_comparison
       from computation import compute_windchill

       # Column names and column indices to read
       columns = {'date':0, 'time':1, 'tempout':2, 'windspeed':7, 'windchill':12}

       # Data types for each column (only if non-string)
       types = {'tempout': float, 'windspeed':float, 'windchill':float}

       # Read data from file
       data = read_data(columns, types=types)

       # Compute the wind chill factor
       windchill = []
       for temp, windspeed in zip(data['tempout'], data['windspeed']):
          windchill.append(compute_windchill(temp, windspeed))

       # Output comparison of data
       print_comparison('WINDCHILL', data['date'], data['time'], data['windchill'], windchill)

    ..

    And for :code:`heatindexcomp.py`\:
    
    .. code-block:: python
       :lineno-start: 1

       from readdata import read_data
       from printing import print_comparison
       from computation import compute_heatindex

       # Column names and column indices to read
       columns = {'date': 0, 'time': 1, 'tempout': 2, 'humout': 5, 'heatindex': 13}
   
       # Data types for each column (only if non-string)
       types = {'tempout': float, 'humout': float, 'heatindex': float}

       # Read data from file
       data = read_data(columns, types=types)

       # Compute the heat index
       heatindex = []
       for temp, hum in zip(data['tempout'], data['humout']):
          heatindex.append(compute_heatindex(temp, hum))

       # Output comparison of data
       print_comparison('HEAT INDX', data['date'], data['time'], data['heatindex'], heatindex)

    ..

23. Stage and commit everything:

    .. code-block:: bash

       $ git stage -a
       $ git commit -m "Creating computation module"

    ..

24. Now, you've got quite a few Python 
    files in the main directory. Which ones are scripts?  
    Which ones are modules meant to be imported?

    Typically, you should group all of the modules 
    meant for import only into another directory called 
    a *package*.  A *package* is a directory containing 
    a file called :code:`__init__.py` inside it.  (Note that
    this file is commonly empty.)

    Create a new directory called :code:`mysci` and 
    create an empty file in it called :code:`__init__.py`\:

    .. code-block:: bash

       $ mkdir mysci
       $ cd mysci
       $ touch __init__.py
       $ cd ..

    ..

    Then, move the 3 modules into this package:

    .. code-block:: bash

       $ git mv readdata.py mysci/
       $ git mv printing.py mysci/
       $ git mv computation.py mysci/

    ..

    Then, let's modify the import statements at the 
    top of our two scripts so that the modules are 
    automatically imported from the new package:

    .. code-block:: python
       :lineno-start: 1

       from mysci.readdata import read_data
       from mysci.printing import print_comparison
       from mysci.computation import compute_heatindex

    ..

25. Stage everything (don't forget the 
    :code:`__init__.py` file!) and commit 

    .. code-block:: bash

       $ git add -a
       $ git commit -m "Creating mysci package"

    ..

    Our commits are getting bigger, but that's okay.  
    Each commit corresponds to a *single* 
    (conceptually) change to the codebase.

    With this last change, our project should look 
    like this (ignoring the
    :code:`__pycache__` directories:

    .. code-block:: bash

       NCAR_python_tutorial_2020/

          data/
             wxobs20170821.txt

          mysci/
             __init__.py
             readdata.py
             printing.py
             computation.py

          heatindexcomp.py
          windchillcomp.py
    ..

26. As a brief aside --
    look at the use of the computation
    functions in these scripts.  

    In the case of the wind chill factor computation,
    it looks like this:

    .. code-block :: python
       :lineno-start: 14

       # Compute the wind chill factor
       windchill = []
       for temp, windspeed in zip(data['tempout'], data['windspeed']):
          windchill.append(compute_windchill(temp, windspeed))
    ..

    This divides the initialization of the :code:`windchill` 
    variable as an empty :code:`list` from the "filling" 
    of that :code:`list` with computed values.

    Python gives you some shortcuts to doing this 
    via a concept called  "comprehensions", which 
    are ways of initializing containers (:code:`list`\s,
    :code:`dict`\s, etc.) with an *internal loop*.  For 
    example, we could have written the previous 3 
    lines in the form of a "one-liner" like so:

    .. code-block:: python
       :lineno-start: 14

       # Compute the wind chill factor
       windchill = [compute_windchill(t, w) for t, w in zip(data['tempout'], data['windspeed'])]

    ..

    This is a *list comprehension*, and it 
    initializes the entire list with the computed 
    contents, rather than initializing an empty list 
    and appending values to it after the fact.  
    Computationally, this is actually *more efficient*.

    Use list comprehensions to make the computation 
    steps in both of scripts one-liners.

27. Do a final stage and commit changes 

    .. code-block:: bash

       $ git add -a
       $ git commit -m "Using list comprehensions"

    ..

-----

That concludes the lesson on "Creating Your First Package", the first in our introduction to Python packages series.

You should now be familiar with modules, using the 
:code:`import` statement, some more :code:`f-string` formatting options,
:code:`__pycache__`\, :code:`.gitignore`\, :code:`.__init__`\, and list 
comprehensions.

.. seealso::
      
   `More information on Python modules <https://docs.python.org/3/tutorial/modules.html>`_
   `More information on on .gitignore <https://git-scm.com/docs/gitignore>`_
   `More information on list comprehension <https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions>`_
   
..

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Using a Built-In Package
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

So far you have created separate :code:`readdata`\, :code:`printing`\, and :code:`computation` modules 
to remove redundant code blocks from your scripts. And you have combined these
modules into a package that we imported into our scripts.

Python comes with many different *built-in* packages (i.e., libraries) that you can import and use.  The
beauty of using built-in packages is that you don't have to install anything new!  If you can use and run
Python, you already have access to these packages.  For this tutorial, we are going to cover just a little 
bit of the built-in :code:`math` package, which extends the computational capabilities beyond the basic math operators we've already covered.

1. Open your terminal, navigate to your :code:`python_tutorial` directory and activate the corresponding environment.

2. Now we're going to add a function for calculating dew point temperature to your :code:`computation.py` module:

   The formula for this is:

   .. math::

      \Gamma = \log{(h)} + \frac{b * t}{c + t}

   ..

   .. math::

      \textit{DPT} = \frac{c * \Gamma}{b - \Gamma}

   ..

   Where *DPT* represents Dew Point Temperature in Degrees C, *h* is humidity in %, *t* is temperature is in degrees C, *a* = 6.112 mbar, *b* = 18.678, and *c* = 257.14 degrees C.

   In order to compute a natural logarithm, we will need to import the :code:`math` package.
   It is best practice to import packages and modules at the beginning (top) of the file.

   .. code-block::
      :lineno-start: 1

      import math

   ..

   To access the logarithmic function within the module :code:`math` you would type :code:`math.log`\.

   Then write the function at the bottom of :code:`computation.py` file (with best practice suggesting 2 empty lines between each function):

   .. code-block::
      :lineno-start: 53

      def compute_dewpoint(t, h):
         """
         Compute the dew point temperature given the temperature and humidity

         Parameters:
            t: The temperature in units of F
            h: The relative humidity in units of %
         """

         tempC = (t - 32) * 5 / 9 # Convert temperature from deg F to deg C
         rh = h / 100
    
         a = 6.112 # mbar
         b = 18.678
         c = 257.14 # deg C

         gamma = math.log(rh) + (b * tempC) / (c + tempC)
         tdp = c * gamma / (b - gamma)

         tdp_F = 9 / 5 * tdp + 32 # Convert deg C to deg F
         return tdp_F
   ..

   This function converts our input temperature to degrees Celsius and humidity to relative humidity,
   specifies the constants, calculates the dew point temperature, and finally converts that temperature to degrees Fahrenheit.

3. Git add and commit :code:`computation.py`\:

   .. code-block:: bash
      
      $ git add computation.py
      $ git commit -m "Function for Computing DPT"

   ..

4. Make a copy of your second script with the new name `dewpointtempcomp.py`:

   .. code-block:: bash

      $ cp windchillcomp.py dewpointtempcomp.py

   ..

5. Git add and commit :code:`dewpointtempcomp.py`\:

   .. code-block:: bash
   
      $ git add dewpointtempcomp.py
      $ git commit -m "Creating a 3rd Script or DPT calculation"

   ..

6. Edit :code:`dewpointtempcomp.py`\:

   Make changes to the import statements to include:

   .. code-block:: python
      :lineno-start: 3

      from mysci.computation.py import compute_dewpoint

   ..

   And change your :code:`columns` and :code:`types` dictionaries to include :code:`dewpt`\:

   .. code-block:: python
      :lineno-start: 5

      # Columns names and column indices to read
      columns = {'date':0 , 'time':1, 'tempout':2, 'humout':5, 'dewpt':6}

      # Data types for each column (only if non-string)
      types = {'tempout':float, 'humout':float, 'dewpt':float}

   ..

   And finally, make changes to the function calls:

   .. code-block:: python
      :lineno-start: 14

      # Compute the dew point temperature
      dewpointtemp = [compute_dewpoint(t, h) for t, h in zip(data['tempout'], data['humout'])]

      # Output comparison of data
      print_comparison('DEW PT', data['date'], data['time'], data['dewpt'], dewpointtemp)

   ..

7. Git add and commit:

   .. code-block:: bash

      $ git add dewpointtempcomp.py
      $ git commit -m "Computed dew point temperature"

   ..

8. Let's learn more about the math module!

   Since you already imported code from your :code:`readdata`\, :code:`printing`, and :code:`computation` modules, importing from the built-in package :code:`math` seemed a little less intimidating.

   So far you have only used the :code:`math.log` function, but let's test out some other common methods within :code:`math`\.

   Perhaps you want to change the base of your logarithm. To do this you could type :code:`math.log(x, base)`. Here :code:`base` is
   a keyword argument (just like :code:`filename` or :code:`types` in our :code:`read_data()` function) which
   means that :code:`base` does not need to be specified.  When it is not specified, the logarithm is assumed to
   be natural (base *e*). When both arguments are entered, the function returns the logarithm of :code:`x` to
   the given :code:`base`\, 
   calculated by :code:`log(x)/log(base)`\. Let's test this out:

   .. code-block:: python

      import math as m

      x = m.e

      y_natural = m.log(x)
      y_base10 = m.log(x, 10)

      print(x, y_natural, y_base10)

   ..

   Something new that we have done here is use the \":code:`import ... as ...`\" statement. This essentially allows us to 
   shorten the name of the module for convenience if it is very long or if we are going to be calling it a lot.

   The symbol :code:`math.e` represents Euler's number (*e*), the base of the natural logarithm. Euler's number (*e*) is an irrational number with infinite decimal places, often approximated as 2.718. 
   How much more accurate is :code:`math.e` than this approximation?
   
   The function :code:`math.log(x, base)` is very useful for computing logarithms in any base - but
   for some common bases there are separate logarithmic functions. 
   Try using :code:`log10(x)`\:

   .. code-block:: python

      import math as m

      x = m.e

      y_natural = m.log(x)
      y_base10 = m.log(x, 10)
      y_log10 = m.log10(x)

      print(x, y_natural, y_base10, y_log10)

   ..

   Do the two values differ? The :code:`math.log10(x)` function is considered to be more accurate than :code:`math.log(x, 10)`\.
   Similarly :code:`math.log2(x)` is more accurate than :code:`math.log(x, 2)`\.

9. Let's cover some :code:`math` trigonometry examples!

   The math symbol :math:`\pi` is an irrational number (like *e*) that is approximately :math:`\frac{22}{7}` or 3.14159. 
   We can access the most accurate :code:`float` version of this number (depending on your C compiler), with :python:`math.pi`\.

   Say we wanted to convert a number from 60 degrees to radians. We have two options:

   .. code-block:: python

      import math as m

      deg = 60

      rads = deg * m.pi / 180
      rads_fromfunc = m.radians(deg)

      print(deg, m.pi, rads, rads_fromfunc)

   ..

   In the first example we used :python:`math.pi` to perform our calculation (by default printed to 15 digits). In the second conversion, 
   we used the function :code:`math.radians(x)` which converts angle x from degrees to radians.

   We can also use trigonometric functions: :code:`math.sin` to get the sine value of an angle, :code:`math.cos` to get the cosine, 
   :code:`math.tan` for the tangent, :code:`math.asin` for the arc sine, :code:`math.acos` to get the arc cosine, and :code:`math.atan` to get the arc tangent. 
   You can also calculate the hypotenuse of a triangle with :code:`math.hypot()`\.
   The input angle for each of these functions must be in radians to get the expected result!

   .. code-block:: python

      import math as m

      deg = 180

      cos_deg = m.cos(deg)
      cos_rad = m.cos(m.radians(60))

      print(cos_deg, cos_rad)

   ..

   You might remember that the cosine of 180 degrees is -1, you can see that we only get the correct value if we enter the degree in radians (180 deg = PI radians).

10. Let's use :code:`math.factorial()`:

    Another popular :code:`math` function is :code:`factorial()` which is much faster and requires a lot less code than writing your own :code:`for` loops to find the factorial of a number.
    Try :code:`math.factorial(5)` and see what you get!

-----

That concludes the "Using a Built-In Package" section of this tutorial.
You should now be familiar with importing packages that you did not build and some methods within the :code:`math` module - 
specifically the :code:`log` method.

.. seealso::
      
   `More information on the Math module <https://docs.python.org/3/library/math.html>`_
   
..
