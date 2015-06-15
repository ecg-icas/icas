.. index:: GET /region
.. _get_region:

GET /region
=============

**Required Scope:** ``api_ro`` or ``console_ro``

This URL returns the region tree or parts of it starting from the **root
node**. The **root node** is a region node in which you cannot place any
ads.

The ``levels`` parameter specifies how many levels starting from
the current one you want to retrieve. The default is 0 which means that only
the root region is returned. To retrieve all sub levels specify a
negative number, e.g. -1.


Parameters
----------

====================    ========    ================================================================================
Name                    Type        Description
====================    ========    ================================================================================
levels                  int         The number of sub region levels to return. Use -1 for all. The default is 0.
_include                string      Comma-separated-list of fields to include. Optional, default is all fields.
_exclude                string      Comma-separated-list of fields to omit. Optional, default empty.
====================    ========    ================================================================================

Errors
------

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
levels                  2001    invalid argument            not a valid number
====================    ====    =======================     ==============================================================================

Example
-------

.. include:: ../examples/region-example.rst
