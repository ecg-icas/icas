.. index:: GET /regions
.. _get_regions:

GET /regions
==================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.region.list-v1+json, application/json``

This URL returns the a map of id to regions in the format described in
:ref:`regions` for the id's requested in parameter ``regionIds``.
This parameter is a comma separated list of integers.
If the parameter ``regionIds`` contains invalid data, i.e. not a positive
integer, the server returns **400 Bad Request**.

Parameters
----------

====================    ========    ================================================================================
Name                    Type        Description
====================    ========    ================================================================================
regionIds               string      Comma-separated-list of integer id's to get regions for.
_include                string      Comma-separated-list of fields to include. Optional, default is all fields.
_exclude                string      Comma-separated-list of fields to omit. Optional, default empty.
====================    ========    ================================================================================

Errors
------

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
regionIds               2000    missing argument            The parameter needs to be present
regionIds               2001    invalid argument            The comma-separated-list contains one or more non-integer values
regionIds               2004    too short                   The value needs to be non-empty
====================    ====    =======================     ==============================================================================

Example
-------

.. include:: ../examples/get-regions-example.rst
