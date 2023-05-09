.. index:: GET /region/{id}
.. _get_region_id:

GET /region/{id}
==================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.region-v1+json, application/json``

This URL returns the region tree or parts of it starting from the node
with the given region ``id``. If the region does not exist the server
returns **404 Not Found**. If the ``id`` is invalid, i.e. not a positive
integer the server returns **400 Bad Request**.

The ``levels`` parameter specifies how many levels starting from
the current one you want to retrieve. The default is 0 which means that only
the current level is being returned. To retrieve all sub levels specify a
sufficiently large number, e.g. 9999.

Parameters
----------

====================    ========    ================================================================================
Name                    Type        Description
====================    ========    ================================================================================
levels                  int         The number of sub region levels to return. The default is 0.
_include                string      Comma-separated-list of fields to include. Optional, default is all fields.
_exclude                string      Comma-separated-list of fields to omit. Optional, default empty.
====================    ========    ================================================================================

Errors
------

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
id                      2001    invalid argument            not a valid number
id                      2002    out of range                negative number
levels                  2001    invalid argument            not a valid number
levels                  2002    out of range                negative number
====================    ====    =======================     ==============================================================================

Example
"""""""

.. include:: ../examples/get-region-id-example.rst
