.. index:: POST /image
.. _RFC 2388: http://www.ietf.org/rfc/rfc2388.txt
.. _post_image:

POST /image
===========

This URL allows uploading of images.
An image upload request must be a multipart form-data request as specified in `RFC 2388`_.

.. note::

    The maximum image size is **8MB** and the supported image formats are: **PNG**, **GIF** and **JPG**.

All images are converted to **JPG** with a maximum dimensions of **1024x1024** while the aspect ratio is maintained.

On success the server returns map with the name and a unique identifier for that image. The name is taken from the
``name`` parameter of the ``Content-Disposition`` header.

The unique identifier is then used to either fetch the image via :ref:`get_image` or save it with a :ref:`post_ad` or
a :ref:`put_ad_id` request.

.. note::

    Images which are not saved are removed after **30 minutes**.


If the request contains invalid images, the server returns **400 Bad Request** with a list of errors.

Errors
------

====    ========================    ==============================================================================
Code    Error message               Description
====    ========================    ==============================================================================
2001    invalid argument            the uploaded image is empty
2008    file too large              file size exceeds the allowed maximum
2018    invalid image format        the image format is not **PNG**, **GIF** or **JPG**
====    ========================    ==============================================================================

Example
-------

.. include:: ../examples/post-image-example.rst