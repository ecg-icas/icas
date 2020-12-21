.. index:: GET /campaign/byVendor/{vendorId}
.. _get_campaign_vendorid:

GET /campaign/byVendor/{vendorId}
===================================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.campaign-v2+json``


Returns a single campaign with the given ``vendorId``.

If the campaign does not exist or does not belong to the user the server returns
**404 Not Found**. If the ``vendorId`` is bigger than 64 characters the
server returns **400 Bad Request**.

The vendorId is unique for a user; It is not possible for a single user to create
multiple campaigns with the same vendorId (even if other campaigns are in status ``DELETED``).

Example
-------

.. include:: ../examples/get-campaign-by-vendorid-v2-example.rst


The full campaign payload model that you get as a response, has the following structure:

.. include:: ../examples/campaign-response.rst
