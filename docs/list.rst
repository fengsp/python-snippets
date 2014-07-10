List
====

Snippets on list manipulation.


`check if a list is empty`_
---------------------------

::
    
    if not a:
        print "List is empty"


`append vs extend`_
-------------------

append::

    x = [1, 2, 3]
    x.append([4, 5])
    # [1, 2, 3, [4, 5]]

extend::
    
    x = [1, 2, 3]
    x.extend([4, 5])
    # [1, 2, 3, 4, 5]


`split a list into evenly sized chunks`_
----------------------------------------

Here's a generator that yields the chunks you want::
    
    def chunks(l, n):
        """ Yield successive n-sized chunks from l.
        """
        for i in xrange(0, len(l), n):
            yield l[i:i+n]


`finding the index of an item`_
-------------------------------

::
    
    >>> ["foo","bar","baz"].index('bar')
    1


`sort a list of dictionaries by values of the dictionary`_
----------------------------------------------------------

::
    
    newlist = sorted(list_to_be_sorted, key=lambda k: k['name'])


`randomly select an item from a list`_
--------------------------------------

::
    
    import random

    foo = ['a', 'b', 'c', 'd', 'e']
    random.choice(foo)


.. _check if a list is empty: http://stackoverflow.com/questions/53513/best-way-to-check-if-a-list-is-empty
.. _append vs extend: http://stackoverflow.com/questions/252703/python-append-vs-extend
.. _split a list into evenly sized chunks: http://stackoverflow.com/questions/312443/how-do-you-split-a-list-into-evenly-sized-chunks-in-python
.. _finding the index of an item: http://stackoverflow.com/questions/176918/finding-the-index-of-an-item-given-a-list-containing-it-in-python
.. _sort a list of dictionaries by values of the dictionary: http://stackoverflow.com/questions/72899/how-do-i-sort-a-list-of-dictionaries-by-values-of-the-dictionary-in-python
.. _randomly select an item from a list: http://stackoverflow.com/questions/306400/how-do-i-randomly-select-an-item-from-a-list-using-python
