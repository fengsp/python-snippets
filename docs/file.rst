File
====

Snippets about files manipulation.


`Unicode (utf8) reading and writing to files`_
-----------------------------------------------

It is easier to use the open method from the codecs module::

    >>> import codecs
    >>> f = codecs.open("test", "r", "utf-8")
    >>> f.read()


.. _Unicode (utf8) reading and writing to files: http://stackoverflow.com/questions/491921/unicode-utf8-reading-and-writing-to-files-in-python
