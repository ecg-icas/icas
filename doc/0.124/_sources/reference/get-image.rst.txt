.. index:: GET /image/{hash}
.. _get_image:

GET /image/{id}
===============

.. list-table::
 :widths: 20 80

 * - Scope
   - ``console_ro``

 * - Accept
   - ``image/*, application/json``

This URL retrieves an image uploaded via :ref:`post_image` by the same user.
The *id*  is the unique identifier provided by the :ref:`post_image` response.

If the image exists and belongs to the user the server sends **200 OK** and the image.
If the image does not exist the server returns **404 Not Found**.

.. note::

    Images which have not been saved with an ad are removed after **30 minutes**.


Example
"""""""

.. include:: ../examples/get-image-example.rst

