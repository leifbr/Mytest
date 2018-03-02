F5 Agility Lab Template
=======================

Introduction
------------

This repo contains a template that should be used when creating lab
documentation for F5's Agility Labs.

Setup
-----

#. Download or ``git clone`` the f5-agility-lab-template

   - ``git clone https://github.com/0xHiteshPatel/f5-agility-lab-template``

#. Download and install Docker CE (https://docs.docker.com/engine/installation/)
#. Build the sample docs ``./containthedocs-build.sh``. The first time you build
   a container (~1G in size) will be downloaded from Docker Hub.
#. Open the ``docs/_build/html/index.html`` file on you system in a web browser

   - ``For example: file:///f5-agility-lab-template/docs/_build/html/index.html``

#. This will give you examples of the class and module layout, ReSTructure (.rst) text examples and syntax.  
#. To get a better idea of where the ``.rst`` files reside, how new classes and modules are created go the **Creating and Building Classes** section below.

Build Scripts
-------------

The repo includes build scripts for common operations:

- ``containthedocs-bash.sh``: Run to container with a BASH prompt
- ``containthedocs-build.sh``: Build HTML docs using ``make -C docs html`` to
  ``docs/_build/html``
- ``containthedocs-clean.sh``: Clean the build directory using
  ``make -C docs clean``
- ``containthedocs-cleanbuild.sh``: Clean the build directory and build HTML
  docs using ``make -C docs clean html``
- ``containthedocs-convert.sh``: Convert a Word ``.docx`` file to rST
- ``containthedocs-pdf.sh``: Build PDF docs using ``make -C docs latexpdf`` to
  ``docs/_build/latex``

Preparing to Build a New Class (lab guide)
------------------------------------------
 
Building a new class/lab guide:

#. Copy contents of the **f5-agility-lab-template** repo to a new directory (new repo)
   - ``cp -Rf <f5-agility-lab-template directory> /path/to/your/newclass``
#. Go to your new directory/repo
   - ``cd /path/to/your/newclass``
#. Edit the``docs/conf.py``
#. Modify the following lines:

   - ``classname = "Your Class Name"``
   - ``github_repo = "https://github.com/f5devcentral/your-class-repo"``

#. Build docs ``./containthedocs-build.sh`` (*see* **Build Scripts** *below*)
#. Open the ``docs/_build/html/index.html`` file on you system in a web browser
#. Create/edit the ``*.rst`` files as needed for your class (*see* **Creating and Building Classes** *below*)

![Default-Lab-Page](/readme-images/default-lab-page.jpg)

#. Check your work as you make changes by running:
    - ``./containthedocs-build.sh``
       - This will rebuild the the html files from the RsT files

Converting from Microsoft Word
------------------------------

You can convert a ``.docx`` file from Microsoft Work to reStructuredText to begin building the class/lab:

#. Copy your ``.docx`` file into the f5-agility-lab-template class directory you built
#. Run ``./containthedocs-convert.sh <filename.docx>``
#. Your converted file will be named ``filename.rst``
#. Images in your document will be extracted and placed in the ``media`` in the f5-agility-lab-template class directory you built. 

.. WARNING:: While the document has been converted to rST format you will still
   need to refactor the rST to use the structure implemented in this template. In otherwords, you will have to edit the **.rst** file for conversion errors and to correctly point to the images.
   
Creating or Building a Class
----------------------------

These are the ReSTructured text files used to create the lab(s) HTML files.

![Lab_RsT_Files](/readme-images/lab-rest-files.jpg)

#. Want to add a new class/lab to your cloud document.  Create a new class directory and class RsT file:

    - ``mkdir /<repo-path>/docs/class**X**``
    - ``cp /repo-path/docs/class1/class1.rst /<repo-path>/docs/class**X**/class**X**.rst``

#. Want to add a module to your class.  Create a new module directory and module RsT file:

    - ``mkdir /<repo-path>/docs/class**X**/moduleX``
    - ``cp /repo-path/docs/class1/classX.rst /<repo-path>/docs/class**X**/class**X**.rst``

