Dictionary
==========

Snippets on dict manipulation.


`merge (union) two Python dictionaries`_
----------------------------------------

::
    
    >>> x = {'a':1, 'b': 2}
    >>> y = {'b':10, 'c': 11}
    >>> z = dict(x.items() + y.items())
    >>> z
    {'a': 1, 'c': 11, 'b': 10}


`create a dictionary with list comprehension`_
----------------------------------------------

In Python 2.6 (or earlier), use the dict constructor::

    d = dict((key, value) for (key, value) in sequence)

In Python 2.7+ or 3, you can just use the dict comprehension syntax directly::

    d = {key: value for (key, value) in sequence}


.. _merge (union) two Python dictionaries: http://stackoverflow.com/questions/38987/how-can-i-merge-union-two-python-dictionaries-in-a-single-expression
.. _create a dictionary with list comprehension: http://stackoverflow.com/questions/1747817/python-create-a-dictionary-with-list-comprehension
