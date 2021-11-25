.. index:: GET /feed/import/{id}/detail

.. _get_feed_import_id_detail:

GET /feed/import/{id}/detail
============================

:ref:`get_feed_import_id_detail_v2`

.. _get_feed_import_id_detail_v2:

GET /feed/import/{id}/detail V2
-------------------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.feedimportdetail-v2+json, application/json``

This endpoint provides a summary of the feed import. Use this endpoint to get information on whether there were any
errors or warnings associated with a specific import.

===================  ======= ====================================
Field                Type    Description
===================  ======= ====================================
id                   int     import ID, same as provided in the call.
url                  string  URL where the feed file was downloaded.
status               string  status of the feed import. See :ref:`get_feed_import_id_detail_v2_status` for details.
dateCreated          string  ISO 8601 date of when the feed import was started.
error                string  the error affecting the whole feed import, as opposed to ``errors`` containing errors affecting individual ads. If your feed is in status ``REJECTED`` this should have the reason.
totalRecordsRead     int     the total number of ads found in the feed file.
recordsSucceeded     int     the number of ads processed without errors.
recordsWithWarnings  int     the number of ads processed with warnings.
recordsFailed        int     the number of ads rejected due to errors.
warnings             object  contains count and a subset of vendorIDs (max 100) of ads having ``warning`` messages, see :ref:`message_struct`.
errors               object  contains count and a subset of vendorIDs (max 100) of ads having ``error`` messages, see :ref:`message_struct`.
===================  ======= ====================================


.. _message_struct:

Error / Warning messages
~~~~~~~~~~~~~~~~~~~~~~~~

===============    ============ ====================================
Field              Type         Description
===============    ============ ====================================
count              int          total number of ads affected by this error/warning message
vendorIdsSample    list<string> subset (max 100) of vendorIDs that were affected by this error
===============    ============ ====================================

It is not possible to fetch all affected ad ids.

.. _get_feed_import_id_detail_v2_status:

Import Status
~~~~~~~~~~~~~

============    =================================================
Status          Description
============    =================================================
PENDING         the feed import is currently processing.
DONE            the feed import has completed successfully. Individual ads could still have failed updating, but the process completed.
REJECTED        the feed import failed; either the feed file could not be downloaded or the feed file didn't pass validation. This means NO ads have been processed.
============    =================================================

In the case the feed import has status ``REJECTED``, the ``error`` field contains the error message that has prevented
the feed import from succeeding. Most of the time this is either a failure to download the feed file, or the feed file didn't pass validation.

Errors
~~~~~~

.. note::

    The endpoint returns **404 Not Found** when import details are requested for:

    - an unknown feed import id for the user

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
id                      2001    invalid argument            not a valid number
id                      2002    out of range                less than 0
====================    ====    =======================     ==============================================================================

Example
~~~~~~~

This is example output of a successful feed import, with some records resulting in warnings/errors:

.. include:: ../examples/get-feed-import-id-detail-v2.rst


This is example output of a failed feed import, where XML validation did not succeed:

.. include:: ../examples/get-feed-import-id-detail-v2-failure.rst

This is example output of a failed feed import, where the feed file could not be downloaded:

.. include:: ../examples/get-feed-import-id-detail-v2-404.rst
