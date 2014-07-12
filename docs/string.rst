String
======

Snippets on string manipulation.


`check if a string is a number`_
--------------------------------

::
    
    >>> a = "123"
    >>> a.isdigit()
    True
    >>> b = "123abc"
    >>> b.isdigit()
    False


`reverse a string`_
-------------------

::
    
    >>> 'hello world'[::-1]
    'dlrow olleh'


write long string
-----------------

If you follow PEP8, there is a maximum of 79 characters limit, BTW, you should
follow PEP8, :)

::
    
    string = ("this is a "
              "really long long "
              "string")


number with leading zeros
-------------------------

::
    
    >>> "%02d" % 1
    '01'
    >>> "%02d" % 100
    '100'
    >>> str(1).zfill(2)
    '01'
    >>> str(100).zfill(2)
    '100'
    >>> int('01')
    1


.. _check if a string is a number: http://stackoverflow.com/questions/354038/how-do-i-check-if-a-string-is-a-number-in-python
.. _reverse a string: http://stackoverflow.com/questions/931092/reverse-a-string-in-python
