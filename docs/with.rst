Context Manager
===============

Snippets about with blocks.


Open And Close Files
--------------------

::
    
    with open('data.txt') as f:
        data = f.read()


Threading Locks
---------------

::

    lock = threading.Lock()

    with lock:
        print 'do something'


Ignore Exceptions
-----------------

:: 
    
    from contextlib import contextmanager

    @contextmanager
    def ignored(*exceptions):
        try:
            yield
        except exceptions:
            pass

    with ignored(ValueError):
        int('string')


Assert Raises
-------------

This one is taken from Flask source::

    from unittest import TestCase

    class MyTestCase(TestCase):
        def assert_raises(self, exc_type):
            return _ExceptionCatcher(self, exc_type)

    class _ExceptionCatcher(object):

        def __init__(self, test_case, exc_type):
            self.test_case = test_case
            self.exc_type = exc_type

        def __enter__(self):
            return self

        def __exit__(self, exc_type, exc_value, tb):
            exception_name = self.exc_type.__name__
            if exc_type is None:
                self.test_case.fail('Expected exception of type %r' %
                                    exception_name)
            elif not issubclass(exc_type, self.exc_type):
                reraise(exc_type, exc_value, tb)
            return True

    class DictTestCase(MyTestCase):

        def test_empty_dict_access(self):
            d = {}
            with self.assert_raises(KeyError):
                d[42]
