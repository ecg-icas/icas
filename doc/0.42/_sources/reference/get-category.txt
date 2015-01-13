.. index:: GET /category
.. _get_category:

GET /category
=============

This URL returns the category tree or parts of it starting from the **root
node**. The **root node** is a category node in which you cannot place any
ads.

The ``subcategoryLevels`` parameter specifies how many levels starting from
the current one you want to retrieve. The default is 0 which means that only
the root category is returned. To retrieve all sub levels specify a
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
subCategoryLevels       2001    invalid argument            not a valid number
subCategoryLevels       2002    out of range                negative number
====================    ====    =======================     ==============================================================================

Example
-------

.. include:: ../examples/category-example.rst