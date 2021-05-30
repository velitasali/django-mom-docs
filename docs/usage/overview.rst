Overview
========

Let's assume that you have the following Django database model:

.. code-block:: python
  :name: models.py
  :caption: myapp/models.py
  
  from django.db import models

  class Post(models.Model):
      title = models.CharField(max_length=100, )
      date = models.DateTimeField()
      slug = models.SlugField(unique=True, )
      
In your `mom.yaml` file, you can refer to this model like this:

.. code-block:: yaml
  :name: mom.yaml
  :caption: mom_data/mom.yaml
  
  mom:
    map:
      post:
        model: myapp.models.Post
        lookupField: slug
        
The ``post`` key in which we have ``model`` and ``lookupField`` keys is the 
name prefix for files that MOM will load and use.

As an example, we will create a serialization file that will target the 
``myapp.models.Post`` model:

.. code-block:: yaml
  :name: post.first-post.yaml
  :caption: mom_data/post.first-post.yaml
  
  field:
    title: My Awesome Title
    date: 2021-06-25 13:00

As you can see, we don't have the ``slug`` field here. This is because 
``lookupField`` sets what the root name is going to be used for. In that
case, ``first-post`` will be the value of the ``slug`` field. 

Now, you can run the MOM command:

.. code-block:: bash

  $ ./manage.py mom
  
This will create the database row or update the existing row after you change 
the any of the values in the file and run the MOM command like above.
