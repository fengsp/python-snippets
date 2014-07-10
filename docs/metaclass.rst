Metaclass
=========

Snippets about metaclasses.


Metaclasses 101
---------------

In Python, everything is one object.  Take CPython for example, we have
PyObject, everything else is inherited from it, and each PyObject has one type
attribute, PyTypeObject, actually PyTypeObject is one PyObject by itself too,
so PyTypeObject has one type attribute, PyTypeType, PyTypeType has type
attribute too, which is PyTypeType itself.  So come back to Python, we have
object, each object has one type, and the type of ``type`` is ``type``. 

Ok, in Python, everything is simple, so you can just treat metaclass as the
class that creates a class.  This is useful for post-processing classes, and
is capable of much more magic(Dangerous though)::

    class ManglingType(type):
        def __new__(cls, name, bases, attrs):
            for attr, value in attrs.items():
                if attr.startswith("__"):
                    continue
                attrs["foo_" + attr] = value
                del attrs[attr]
            return type.__new__(cls, name, bases, attrs)

    class MangledClass:
        __metaclass__ = ManglingType

        def __init__(self, value):
            self.value = value

        def test(self):
            return self.value

    mangled = MangledClass('test')

::

    >>> mangled.test()
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    AttributeError: 'MangledClass' object has no attribute 'test'
    >>> mangled.foo_test()
    'test'
