Installation
============

First, install the latest version of MOM:

.. code-block:: bash

   $ python3 -m pip install django-mom
   
Next, add ``django-mom`` to the ``INSTALLED_APPS`` list in your Django 
app's **settings.py** file:

.. code-block:: python
   :caption: myapp/settings.py
   :emphasize-lines: 3

   INSTALLED_APPS = [
       'django.contrib.staticfiles',
       'django_mom',
   ]
  
Now you are ready to use MOM in your app. To test it, (after 
setting up Django and making sure it works) you can run:

.. code-block:: bash

   $ ./manage.py mom
   
This should output something similar to this: 
``Couldn't open 'mom_data/mom.yaml' file.`` which is the expected output if you
haven't worked with MOM before. 

Next, we will create the `mom_data` folder which is the default folder where 
MOM related files are put. It should be in the root folder of your Django app. 
You can customize the path by setting ``MOM_FOLDER`` to your liking.

You can also override the ``MOM_FILE`` variable that is used for pattern 
matching when looking for MOM related files. It is set to `mom.yaml` by 
default.

With custom paths, your settings file will look like this:

.. code-block:: python
   :caption: myapp/settings.py

   MOM_FOLDER = 'mom_data'
   MOM_FILE = 'mom.yaml'

