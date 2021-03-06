Iterator And Generator
======================

Snippets about iterators and generators.


`iterator - the Python yield keyword explained`_
------------------------------------------------

Iterables::

    >>> mylist = [x*x for x in range(3)]
    >>> for i in mylist:
    ...    print(i)
    0
    1
    4

Generators are iterators, but you can only iterate over them once. It's
because they do not store all the values in memory, they generate the values
on the fly::
    
    >>> mygenerator = (x*x for x in range(3))
    >>> for i in mygenerator:
    ...    print(i)
    0
    1
    4

Yield is a keyword that is used like return, except the function will return
a generator::
    
    >>> def createGenerator():
    ...    mylist = range(3)
    ...    for i in mylist:
    ...        yield i*i
    ...
    >>> mygenerator = createGenerator() # create a generator
    >>> print(mygenerator) # mygenerator is an object!
    <generator object createGenerator at 0xb7555c34>
    >>> for i in mygenerator:
    ...     print(i)
    0
    1
    4


`how do I determine if an object is iterable`_
----------------------------------------------

Duck typing::
    
    try:
        iterator = iter(theElement)
    except TypeError:
        # not iterable
    else:
        # iterable

Type checking, need at least Python 2.6 and work only for new-style classes::
    
    import collections

    if isinstance(theElement, collections.Iterable):
        # iterable
    else:
        # not iterable


.. _iterator - The Python yield keyword explained: http://stackoverflow.com/questions/231767/the-python-yield-keyword-explained
.. _how do I determine if an object is iterable: http://stackoverflow.com/questions/1952464/in-python-how-do-i-determine-if-an-object-is-iterable
