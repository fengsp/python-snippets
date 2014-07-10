Performance
===========

Snippets on Python running performance.


`why does Python code run faster in a function`_
------------------------------------------------

You might ask why it is faster to store local variables than globals.  This is
a CPython implementation detail.

Remember that CPython is compiled to bytecode, which the interpreter runs.  When
a function is compiled, the local variables are stored in a fixed-size array
(not a dict) and variable names are assigned to indexes.  This is possible
because you can't dynamically add local variables to a function.  Then
retrieving a local variable is literally a pointer lookup into the list and a
refcount increase on the PyObject which is trivial.

Contrast this to a global lookup (``LOAD_GLOBAL``), which is a true dict search
involving a hash and so on.   Incidentally, this is why you need to specify
global i if you want it to be global: if you ever assign to a variable inside a
scope, the compiler will issue ``STORE_FAST`` for its access unless you tell
it not to.

By the way, global lookups are still pretty optimised.  Attribute lookups
foo.bar are the really slow ones!


.. _why does Python code run faster in a function: http://stackoverflow.com/questions/11241523/why-does-python-code-run-faster-in-a-function
