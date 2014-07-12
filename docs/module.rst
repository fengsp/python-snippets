Module
======

Snippets on packages and modules.


get all module files
--------------------

::
    
    def _iter_module_files():
        for module in sys.modules.values():
            filename = getattr(module, '__file__', None)
            if filename:
                if filename[-4:] in ('.pyc', '.pyo'):
                    filename = filename[:-1]
                yield filename


dynamic module import
---------------------

::
    
    def import_string(import_name):
        """Import a module based on a string.

        :param import_name: the dotted name for the object to import.
        :return: imported object
        """
        if '.' in import_name:
            module, obj = import_name.rsplit('.', 1)
        else:
            return __import__(import_name)
        return getattr(__import__(module, None, None, [obj]), obj)
