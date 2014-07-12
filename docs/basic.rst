Basic
=====

Snippets on basic things.


not None test
-------------

::
    
    if value is not None:
        pass


dump variable
-------------

::
    
    import pprint

    pprint.pprint(globals())


`ternary conditional operator`_
-------------------------------

::
    
    >>> 'true' if True else 'false'
    'true'
    >>> 'true' if False else 'false'
    'false'


`accessing the index in for loops`_
-----------------------------------

::

    for idx, val in enumerate(ints):
        print idx, val


`how do I check if a variable exists`_
--------------------------------------

To check the existence of a local variable::

    if 'myVar' in locals():
        # myVar exists.

To check the existence of a global variable::

    if 'myVar' in globals():
        # myVar exists.

To check if an object has an attribute::

    if hasattr(obj, 'attr_name'):
        # obj.attr_name exists.


.. _ternary conditional operator: http://stackoverflow.com/questions/394809/does-python-have-a-ternary-conditional-operator
.. _accessing the index in for loops: http://stackoverflow.com/questions/522563/accessing-the-index-in-python-for-loops
.. _how do I check if a variable exists: http://stackoverflow.com/questions/843277/how-do-i-check-if-a-variable-exists-in-python
