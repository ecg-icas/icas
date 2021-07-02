.. index:: GET /feed/import/{id}/detail/{vendorId}

.. warning::

	This call is scheduled to be deprecated. Please use :ref:`get_feed_import_id_detail` instead.

.. _get_feed_import_id_detail_vendor_id:

GET /feed/import/{id}/detail/{vendorId}
=======================================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.feedimportdetail-v1+json, application/json``

This endpoint provides :ref:`get_feed_import_id_detail` for an ad during a successful feed import.
**404 Not Found** is returned if no ad can be found with the specified import and vendor ID's.

Errors
~~~~~~

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
id                      2001    invalid argument            not a valid number
id                      2002    out of range                less than 0
vendorId                2005    too long                    longer than the configured tenant's maximum length for vendor ID
====================    ====    =======================     ==============================================================================

Example
~~~~~~~

.. include:: ../examples/get-feed-import-id-detail-vendor-id.rst
