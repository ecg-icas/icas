.. index:: GET /category
.. _get_category:

GET /category
=============

**Required Scope:** ``api_ro`` or ``console_ro``

This URL returns the category tree or parts of it starting from the **root
node**. The **root node** is a category node in which you cannot place any
ads.

The ``levels`` parameter specifies how many levels starting from
the current one you want to retrieve. The default is 0 which means that only
the root category is returned. To retrieve all sub levels specify a
sufficiently large number, e.g. 9999.

.. note::

	The parameter ``subCategoryLevels`` is an alias for ``levels`` and is
	deprecated. It will be removed after September 2015.



Parameters
----------

====================    ========    ================================================================================
Name                    Type        Description
====================    ========    ================================================================================
levels                  int         The number of sub category levels to return. Use 9999 for all. The default is 0.
_include                string      Comma-separated-list of fields to include. Optional, default is all fields.
_exclude                string      Comma-separated-list of fields to omit. Optional, default empty.
====================    ========    ================================================================================

Errors
------

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
levels                  2001    invalid argument            not a valid number
levels                  2002    out of range                negative number
====================    ====    =======================     ==============================================================================

Example
-------

.. include:: ../examples/category-example-v1.rst
