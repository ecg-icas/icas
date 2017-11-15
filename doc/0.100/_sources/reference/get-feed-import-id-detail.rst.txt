.. index:: GET /feed/import/{id}/detail
.. _get_feed_import_id_detail:

GET /feed/import/{id}/detail
============================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.feedimportdetail.list-v1+json, application/json``

This endpoint provides detailed import information for each ad during a successful feed import.
The field ``vendorId`` identifies the ad in the XML feed and can be used in :ref:`get_feed_import_id_detail_vendor_id`.
The ``dateCreated`` shows the time when the ad was processed. The ``warnings`` field contains
a list of descriptive messages when the ad was successfully imported but with warnings,
e.g. the system has normalized the ad's phone number because it is specified in an unsupported
format. The ``errors`` field contains a list of messages to signify why an ad could not be imported.

.. note::

    The field ``vendorId`` maps to the XML field ``externalId`` and is stored for imported ads as :ref:`ad_vendorId`.

Since a feed XML file can contain an arbitrary number of ads, API clients need a way to retrieve
status information for only a subset of all ads. This is achieved by using the ``limit`` and ``offset`` parameters:
``limit`` controls the number of returned entities and ``offset`` allows for skipping entities.

The endpoint returns **404 Not Found** when import details are requested for:

- an unknown feed import
- a **REJECTED** feed import
- a successful feed import of an empty XML document (which contains no ads)

Errors
~~~~~~

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
id                      2001    invalid argument            not a valid number
id                      2002    out of range                less than 0
limit                   2001    invalid argument            not a valid number
limit                   2002    out of range                less than 1 or greater than 100
offset                  2001    invalid argument            not a valid number
offset                  2002    out of range                less than 0
====================    ====    =======================     ==============================================================================

Example
~~~~~~~

.. include:: ../examples/get-feed-import-id-detail.rst
