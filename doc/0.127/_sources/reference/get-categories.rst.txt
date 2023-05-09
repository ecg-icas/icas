.. index:: GET /categories
.. _get_categories:

GET /categories
===============

:ref:`get_categories_v5` | :ref:`get_categories_v1`

.. warning::

    :ref:`get_categories_v1` is now officially deprecated and scheduled for removal on May, 1st 2023. Please move to use :ref:`get_categories_v5`.

This URL returns the a map of id to categories in the format described in
:ref:`categories` for the id's requested in parameter ``categoryIds``.
This parameter is a comma separated list of integers.
If the parameter ``categoryIds`` contains invalid data, i.e. not a positive
integer, the server returns **400 Bad Request**.

.. _get_categories_v5:

GET /categories V5
------------------

GET /categories V5 has the same functionality as V1, except that it returns the categories in V5 format, see :ref:`categories` for details.

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.category.list-v5+json, application/json``

Example
"""""""

.. include:: ../examples/get-categories-v5-example.rst

.. _get_categories_v1:

GET /categories V1
------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.category.list-v1+json, application/json``


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
"""""""

.. include:: ../examples/get-categories-example.rst
