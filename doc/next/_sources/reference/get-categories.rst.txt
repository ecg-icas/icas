.. index:: GET /categories
.. _get_categories:

GET /categories
==================

GET /categories
---------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.category.list-v1+json, application/json``

This URL returns the a map of id to categories in the format described in
:ref:`categories_v2` for the id's requested in parameter ``categoryIds``.
This parameter is a comma separated list of integers.
If the parameter ``categoryIds`` contains invalid data, i.e. not a positive
integer, the server returns **400 Bad Request**.

Parameters
----------

====================    ========    ================================================================================
Name                    Type        Description
====================    ========    ================================================================================
categoryIds             string      Comma-separated-list of integer id's to get categories for.
_include                string      Comma-separated-list of fields to include. Optional, default is all fields.
_exclude                string      Comma-separated-list of fields to omit. Optional, default empty.
====================    ========    ================================================================================

Errors
------

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
categoryIds             2000    missing argument            The parameter needs to be present
categoryIds             2001    invalid argument            The comma-separated-list contains one or more non-integer values
categoryIds             2004    too short                   The value needs to be non-empty
====================    ====    =======================     ==============================================================================

Example
-------

.. include:: ../examples/get-categories-example.rst
