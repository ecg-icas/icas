.. index:: GET /feed/import
.. _get_feed_import:

GET /feed/import
================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.feedimport.list-v1+json, application/json``

This URL returns the feed imports of the current user in descending chronological order.
By default, only the last **10** imports are retrieved but this number can be controlled
via the ``limit`` parameter (< **100**).

Feed imports are triggered automatically by the system once per day or on demand by
Customer Service agents. Each feed import object contains the time when it was started
(``dateCreated``), the URL of the user's XML document (``url``) and whether the
document could successfully be processed (``status``). The ``status`` field contains **DONE**
when the document was processed correctly, **PENDING** - when it is currently being processed
or **REJECTED** - when it was either not accessible or syntactically incorrect. In the latter
case, the field ``error`` contains a descriptive error message.

The feed import object also contains counters to denote the total number of ads specified in the
XML document (``totalCount``), the number of ads which were processed without errors (``okCount``),
the number of ads which were processed with warnings (``warningCount``) and the number of ads which
were rejected due to errors (``errorCount``).

.. note::

    The field ``totalCount`` is set to **-1** when the XML document could not be processed (``status`` = **REJECTED**)

Each feed import contains an ``id`` field which can be used to query for more information regarding
the erroneous ads in the XML document via :ref:`get_feed_import_id_detail`.


Errors
""""""

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
limit                   2001    invalid argument            not a valid number
limit                   2002    out of range                less than 1 or greater than 100
====================    ====    =======================     ==============================================================================

Example
"""""""

.. include:: ../examples/get-feed-import.rst
