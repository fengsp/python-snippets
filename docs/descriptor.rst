Descriptor
==========

Snippets about descriptors.


descriptors 101
---------------

What is descriptor:
    
- __get__
- __set__
- __delete__
- Common descriptors: function, property

Demo::

    >>> class Demo(object):
    ...     def hello(self):
    ...         pass
    ... 
    >>> Demo.hello
    <unbound method Demo.hello>
    >>> Demo.__dict__['hello']
    <function hello at 0x102b17668>
    >>> Demo.__dict__['hello'].__get__(None, Demo)
    <unbound method Demo.hello>
    >>> 
    >>> Demo().hello
    <bound method Demo.hello of <__main__.Demo object at 0x102b28550>>
    >>> Demo.__dict__['hello'].__get__(Demo(), Demo)
    <bound method Demo.hello of <__main__.Demo object at 0x102b285d0>>


data and non-data descriptors
-----------------------------

If an object defines both ``__get__`` and ``__set__``, it is considered a data
descriptor.  Descriptors that only define ``__get__`` are called non-data
descriptors.

Data and non-data descriptors differ in how overrides are calculated with
respect to entries in an instance’s dictionary.  If an instance’s dictionary
has an entry with the same name as a data descriptor, the data descriptor
takes precedence.  If an instance’s dictionary has an entry with the same
name as a non-data descriptor, the dictionary entry takes precedence.

Demo::

    class Demo(object):
    
        def __init__(self):
            self.val = 'demo'

        def __get__(self, obj, objtype):
            return self.val


    class Foo(object):
    
        o = Demo()

::

    >>> f = Foo()
    >>> f.o
    'demo'
    >>> f.__dict__['o'] = 'demo2'
    >>> f.o
    'demo2'

Now we add ``__set__``::

    class Demo(object):
    
        def __init__(self):
            self.val = 'demo'

        def __get__(self, obj, objtype):
            return self.val

        def __set__(self, obj, val):
            self.val = val

::

    >>> f = Foo()
    >>> f.o
    'demo'
    >>> f.__dict__['o'] = 'demo2'
    >>> f.o
    'demo'
    >>> f.o = 'demo3'
    >>> f.o
    'demo3'


better way to write property
----------------------------

Let's just see the code::
    
    class Foo(object):
        
        def _get_thing(self):
            """Docstring"""
            return self._thing

        def _set_thing(self, value):
            self._thing = value

        thing = property(_get_thing, _set_thing)
        del _get_thing, _set_thing


cached property
---------------

Just grab it from django source::
    
    class cached_property(object):
        """
        Decorator that creates converts a method with a single
        self argument into a property cached on the instance.
        """
        def __init__(self, func):
            self.func = func

        def __get__(self, instance, type):
            res = instance.__dict__[self.func.__name__] = self.func(instance)
            return res
