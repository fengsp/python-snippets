Method
======

Snippets about method.


method 101
----------

Instancemethods take ``self`` argument, classmethods take ``cls`` argument,
staticmethods take no magic argument(not very useful).

::
    
    class FancyDict(dict):
        @classmethod
        def fromkeys(cls, keys, value=None):
            data = [(key, value) for key in keys]
            return cls(data)

::
    
    >>> FancyDict(key1='value1', key2='value2', key3='value3')
    {'key3': 'value3', 'key2': 'value2', 'key1': 'value1'}
    >>> FancyDict.fromkeys(['key1', 'key2'], 'value')
    {'key2': 'value', 'key1': 'value'}

We are gonna talk a little more about classes, ``__slots__``, you can use it
to omit dict of python instances and reduce memory use in the end::
    
    class Tiny(object):
        __slots__ = ['value']
        def __init__(self, value):
            self.value = value
    t = Tiny(1)

::

    >>> t.value
    1
    >>> t.value2 = 2
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    AttributeError: 'Tiny' object has no attribute 'value2'

Then talk a little about ``__new__``, this is the actual constructor method
of one instance, and it is one static method::

    class WrappingInt(int):
        __slots__ = []
        def __new__(cls, value):
            value = value % 255
            self = int.__new__(cls, value)
            return self

    wrapping_int = WrappingInt(256)
    
::

    >>> wrapping_int
    1
