Decorator
=========

Snippets about decorators.


decorators 101
--------------

Let's begin with syntactic sugar::

    @EXPR
    def add(a, b):
        return a + b

    # The same thing as

    def add(a, b):
        return a + b
    add = EXPR(add)
    
    @EXPR(ARG)
    def add(a, b):
        return a + b

    # The same thing as

    def add(a, b):
        return a + b
    add = EXPR(ARG)(add)


good decorator
--------------

We want to run a function for certain times::
    
    from functools import wraps
    
    def spam(repeats):
        def decorator(func):
            @wraps(func)
            def wrapper(*args, **kwargs):
                for i in range(repeats):
                    func(*args, **kwargs)
            return wrapper
        return decorator

    @spam(11)
    def talk(word):
        """talk docstring"""
        print word


method decorator
----------------

We need one decorator that makes function to method decorators::

    from functools import update_wrapper

    class MethodDecoratorDescriptor(object):

        def __init__(self, func, decorator):
            self.func = func
            self.decorator = decorator

        def __get__(self, obj, type=None):
            return self.decorator(self.func.__get__(obj, type))

    def method_decorator(decorator):
        def decorate(f):
            return MethodDecoratorDescriptor(f, decorator)
        return decorate

    # usage
    def spam(f):
        def wrapper(value):
            return f(value) + ":spamed"
        return update_wrapper(wrapper, f)

    class MyClass(object):

        @method_decorator(spam)
        def my(self, value):
            return value

    foo = MyClass()
    print foo.my('hello')   
