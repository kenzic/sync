django-rest-url-override-content-negotiation
===================================================

DRF url content type override allows the content type of the request to be overriden by a url parameter.


Why would I need to do this?
=============================
Sometimes the content type sent in the header is not the type that it is. For example, due to limitations in IE9's XHR, it is unable to support CORS. Pollyfills like, `jQuery-ajaxTransport-XDomainRequest`_ get around this by using XDomainRequest, which supports CORS. The problem is XDomainRequest only sends a content type of text/plain in the header. This is problematic when POSTing data. drf_url_content_type_override let's you specify a content type which will override the header value.


.. _`jQuery-ajaxTransport-XDomainRequest`: https://github.com/MoonScript/jQuery-ajaxTransport-XDomainRequest


Install
-------------
.. code-block:: shell
  pip install drf-url-content-type-override

.. code-block:: python
  REST_FRAMEWORK = {
    'DEFAULT_CONTENT_NEGOTIATION_CLASS': 'drf_url_content_type_override.URLOverrideContentNegotiation',
  }


Usage
-------------
.. code-block:: javascript

  jquery.ajax({
    'url': 'http://someotherdomain.com/api/1/contact?_content_type=application/x-www-form-urlencoded',
    'type': 'POST',
    'data': {'name': 'Chris'}
  })





https://github.com/tomchristie/django-rest-framework/pull/1731
