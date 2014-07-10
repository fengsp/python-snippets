Input and Ouput
===============

Snippets about input and output.


`read from stdin`_
------------------

::
    
    import sys

    for line in sys.stdin:
        print line


`print to stderr`_
------------------

::
    
    print >> sys.stderr, 'spam'


.. _read from stdin: http://stackoverflow.com/questions/1450393/how-do-you-read-from-stdin-in-python
.. _print to stderr: http://stackoverflow.com/questions/5574702/how-to-print-to-stderr-in-python
