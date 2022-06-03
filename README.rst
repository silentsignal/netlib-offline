About this fork
---------------

This is a fork of `mitmproxy`_'s old `netlib`_, that included the parts for raw HTTP 
message parsing. The purpose of this fork is to keep the standalone HTTP parser 
alive, other parts will be gradually removed.

While we would be happy to see contributions (improvements, bugfixes) to this 
fork to keep it useful for everyone, we take this "No support, no liability"
thing especially seriously in this case, as we don't have the resources to 
maintain a really popular project. Feature requests will likely be rejected. 

Alternatives
------------

`Cunningham's Law`_ states "the best way to get the right answer on the internet is not to ask a question; it's to post the wrong answer." Shortly after this repo was made public we were made aware of the following alternatives:

* https://dpkt.readthedocs.io/en/latest/api/api_auto.html#module-dpkt.http
* https://h11.readthedocs.io/en/latest/

Basic Usage
-----------

.. code:: python

    from netlib.http.http1 import read_request
    from netlib.http.http1.assemble import assemble_request
    from io import BytesIO

    req = read_request(BytesIO(b"GET / HTTP/1.1\r\nHost: www.example.com\r\n\r\n"))
    req.headers["X-Foo"] = "Bar"

    print(assemble_request(req))


Original intro
--------------

Netlib is a collection of network utility classes, used by the pathod and
mitmproxy projects. It differs from other projects in some fundamental
respects, because both pathod and mitmproxy often need to violate standards.
This means that protocols are implemented as small, well-contained and flexible
functions, and are designed to allow misbehaviour when needed.

.. _mitmproxy: https://github.com/mitmproxy/mitmproxy

.. _netlib: https://github.com/mitmproxy/netlib

.. _Cunningham's Law: https://meta.wikimedia.org/wiki/Cunningham%27s_Law
