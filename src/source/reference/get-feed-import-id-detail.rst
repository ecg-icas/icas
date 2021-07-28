.. index:: GET /feed/import/{id}/detail

.. _get_feed_import_id_detail:

.. _get_feed_import_id_detail_v2:

GET /feed/import/{id}/detail V2
===============================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.feedimportdetail.list-v2+json, application/json``

This endpoint provides a summary of the feed import.

Each feed import object contains the time when it was started
(``accepted``), the URL of the user's XML document (``url``) and whether the
document could successfully be processed (``status``). The ``status`` field

============    =================================================
Status           Description
============    =================================================
PENDING         when it is currently being processed status
 DONE           when the document was processed successfully status
REJECTED        when it was either not accessible or syntactically incorrect status
============    =================================================

In the latter case, the ``error`` field contains the error message that has prevented
the complete feed from being imported.

Import object contains the following fields:

=============  ======= ====================================
Field           Type    Description
=============  ======= ====================================
recordCount     int    the total number of ads found in the XML document
acceptCount     int    the number of ads processed without errors
noticeCount     int    the number of ads processed with warnings
rejectCount     int    the number of ads rejected due to errors
error           string the error affecting the whole feed, as opposed to ``errors`` containing errors affecting individual ads
warnings        struct contains ``warning`` messages indicating data validation issues for successfully imported ads
errors          struct contains messages explaining why an ad could not be imported.
=============  ======= ====================================

Both ``warnings`` and ``errors`` fields contains a subset of a maximum of 100 ad ids for which
the message was generated. It is not possible to fetch all affected ad ids.
For example if 10000 ads had the same validation issue on the ads, the ``warnings`` field
would contain a single warning message describing the issue in more details
and a 100 ad ids of the ads which had this issue.

Another example - if 55 ads failed validation because
of the missing category field, ``errors`` field would contain the detailed validation message and all 55 ad
ids that had the category missing.


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
