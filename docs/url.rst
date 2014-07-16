URL
===

Snippets for url.


url quote
---------

::
    
    from urllib import quote_plus

    quoted = quote_plus(url)


url encode
----------

::
    
    from urllib import urlencode
    
    encoded = urlencode({'key': 'value'})
    encoded = urlencode([('key1', 'value1'), ('key2', 'value2')])
