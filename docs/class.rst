Class
=====

Snippets on classes.


New-style and classic classes
-----------------------------

Classes and instances come in two flavors: old-style and new-style.  For more
details, check out `New-style and classic classes <https://docs.python.org/2/reference/datamodel.html#new-style-and-classic-classes>`_


print a object
--------------

::
    
    Class User(object):
        
        def __init__(self, name):
            self.name = name

        def __repr__(self):
            return '<User %r>' % self.name

        def __str__(self):
            return self.name
