.. index:: GET /category/{id}
.. _get_category_id:

GET /category/{id}
==================

:ref:`scopes` **read**

This URL returns the category tree or parts of it starting from the node
with the given category ``id``. If the category does not exist the server
returns **404 Not Found**. If the ``id`` is invalid, i.e. not a positive
integer the server returns **400 Bad Request**.

The ``subCategoryLevels`` parameter specifies how many levels starting from
the current one you want to retrieve. The default is 0 which means that only
the current level is being returned. To retrieve all sub levels specify a
sufficiently large number, e.g. 9999.

Parameters
----------

====================    ========    ================================================================================
Name                    Type        Description
====================    ========    ================================================================================
subCategoryLevels       int         The number of sub category levels to return. Use 9999 for all. The default is 0.
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
subCategoryLevels       2001    invalid argument            not a valid number
subCategoryLevels       2002    out of range                negative number
====================    ====    =======================     ==============================================================================

Example
-------

.. include:: ../examples/category-example-v1.rst