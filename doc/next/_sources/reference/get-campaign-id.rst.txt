.. index:: GET /campaign/{id}

GET /campaign/{id}
==================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.campaign-v2+json, application/json``


This URL returns a single campaign with the given ``id``.

If the campaign does not exist or does not belong to the user the server returns
**404 Not Found**. If the ``id`` is invalid, i.e. not a positive integer the
server returns **400 Bad Request**.

TODO: table with fields

Example:
--------

.. include:: ../examples/get-campaign-id-v2-example.rst
