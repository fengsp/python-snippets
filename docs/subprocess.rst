Subprocess
==========

Snippets about subprocesses.


`calling an external command`_
------------------------------

::
    
    from subprocess import call
    call(["ls", "-l"])


subprocess input, output and returncode
---------------------------------------

::
    
    from subprocess import Popen, PIPE

    p = Popen(["ls", "-l"], stdin=PIPE, stdout=PIPE, stderr=PIPE)
    std_input = "/"
    out, err = p.communicate(std_input)
    returncode = p.returncode


use string to call subprocess instead of list
---------------------------------------------

::
    
    from subprocess import call
    import shlex
    
    command = "ls -l"
    call(shlex.split(command))


.. _calling an external command: http://stackoverflow.com/questions/89228/calling-an-external-command-in-python
