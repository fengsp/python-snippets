File
====

Snippets about files and folders manipulation.


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


`get file creation & modification date/times`_
----------------------------------------------

ctime() does not refer to creation time on `*nix` systems, but rather the last
time the inode data changed::
    
    import os.path, time
    print "last modified: %s" % time.ctime(os.path.getmtime(file))
    print "created: %s" % time.ctime(os.path.getctime(file))


`find current directory and file's directory`_
----------------------------------------------

::
    os.getcwd()
    os.path.dirname(os.path.realpath(__file__))


`remove/delete a folder that is not empty`_
-------------------------------------------

::
    
    import shutil

    shutil.rmtree('/folder_name')


.. _check if file exists: http://stackoverflow.com/questions/82831/how-do-i-check-if-a-file-exists-using-python
.. _unicode (utf8) reading and writing to files: http://stackoverflow.com/questions/491921/unicode-utf8-reading-and-writing-to-files-in-python
.. _extracting extension from filename: http://stackoverflow.com/questions/541390/extracting-extension-from-filename-in-python
.. _remove/delete a folder that is not empty: http://stackoverflow.com/questions/303200/how-do-i-remove-delete-a-folder-that-is-not-empty-with-python
.. _get file creation & modification date/times: http://stackoverflow.com/questions/237079/how-to-get-file-creation-modification-date-times-in-python
.. _find current directory and file's directory: http://stackoverflow.com/questions/5137497/find-current-directory-and-files-directory
