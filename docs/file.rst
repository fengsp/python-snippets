File
====

Snippets about files manipulation.


`check if file exists`_
-----------------------

If you need to be sure it's a file::
    
    import os.path
    os.path.isfile(filename)


`unicode (utf8) reading and writing to files`_
-----------------------------------------------

It is easier to use the open method from the codecs module::

    >>> import codecs
    >>> f = codecs.open("test", "r", "utf-8")
    >>> f.read()


`extracting extension from filename`_
-------------------------------------

::
    
    import os
    filename, ext = os.path.splitext('/path/to/somefile.ext')


.. _check if file exists: http://stackoverflow.com/questions/82831/how-do-i-check-if-a-file-exists-using-python
.. _unicode (utf8) reading and writing to files: http://stackoverflow.com/questions/491921/unicode-utf8-reading-and-writing-to-files-in-python
.. _extracting extension from filename: http://stackoverflow.com/questions/541390/extracting-extension-from-filename-in-python
