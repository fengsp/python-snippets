HTTP
====

Snippets for http.


simple http web server
----------------------

::
    
    $ python -m SimpleHTTPServer [port]


http get
--------

::
    
    import urllib2
    urllib2.urlopen("http://example.com/").read()


`http head`_
------------

::
    
    >>> import httplib
    >>> conn = httplib.HTTPConnection("www.google.com")
    >>> conn.request("HEAD", "/index.html")
    >>> res = conn.getresponse()
    >>> print res.status, res.reason
    200 OK


http post
---------

::
    
    >>> import httplib, urllib
    >>> params = urllib.urlencode({'key': 'value'})
    >>> headers = {"Content-type": "application/x-www-form-urlencoded",
    ...            "Accept": "text/plain"}
    >>> conn = httplib.HTTPConnection("www.example.com")
    >>> conn.request("POST", "", params, headers)
    >>> response = conn.getresponse()
    >>> print response.status, response.reason
    200 OK
    >>> conn.close()


`http put`_
-----------

::
    
    import urllib2
    opener = urllib2.build_opener(urllib2.HTTPHandler)
    request = urllib2.Request('http://example.org', data='your_put_data')
    request.add_header('Content-Type', 'your/contenttype')
    request.get_method = lambda: 'PUT'
    url = opener.open(request)


.. _http head: http://stackoverflow.com/questions/107405/how-do-you-send-a-head-http-request-in-python
.. _http put: http://stackoverflow.com/questions/111945/is-there-any-way-to-do-http-put-in-python
