.. index:: GET /feed/import/{id}/detail

.. _get_feed_import_id_detail:

GET /feed/import/{id}/detail V2
============================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.feedimportdetail.list-v2+json, application/json``

This endpoint provides summary of the feed import.

Each feed import object contains the time when it was started
(``accepted``), the URL of the user's XML document (``url``) and whether the
document could successfully be processed (``status``). The ``status`` field

contains `0` when it is currently being processed status **PENDING**,

contains `1` when the document was processed successfully status **DONE**,

contains `2` when it was either not accessible or syntactically incorrect status **REJECTED**.

In the latter case, the field ``error`` contains a descriptive error message.
The ``error`` field contains the error message that has affected the whole feed, for example,
it would be populated if the feed xml schema fails validation.

The feed import object also contains counters to denote the total number of ads specified in the
XML document (``recordCount``), the number of ads which were processed without errors (``acceptCount``),
the number of ads which were processed with warnings (``noticeCount``) and the number of ads which
were rejected due to errors (``rejectCount``). The ``warnings`` field contains
``warning`` messages indicating data validation issues for successfully imported ads.
The ``errors`` field contains messages explaining why an ad could not be imported.
Both ``warnings`` and ``errors`` fields contains a subset of a maximum of 100 ad ids for which
the message was generated. It is not possible to fetch all affected ad ids.

For example if 10000 ads had the same validation issue on the ads, the ``warnings`` field
would contain a single warning message describing the issue in more details
and a 100 ad ids of the ads which had this issue.

Another example - if 55 ads failed validation because
of the missing category field, ``errors`` field would contain the detailed validation message and all 55 ad
ids that had the category missing.

To summarize ``error`` is contain error affecting the whole feed, while ``errors`` contains
errors affecting individual ads.

.. note::

The endpoint returns **404 Not Found** when import details are requested for:

- an unknown feed import
- a successful feed import of an empty XML document (which contains no ads)

Errors
~~~~~~

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
id                      2001    invalid argument            not a valid number
id                      2002    out of range                less than 0
====================    ====    =======================     ==============================================================================

Example
~~~~~~~

.. include:: ../examples/get-feed-import-id-detail-v2.rst

GET /feed/import/{id}/detail V1 (depreciated)
============================

.. warning::

	This call is scheduled to be deprecated. Please use :ref:`get_feed_import_id_detail` instead.

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
