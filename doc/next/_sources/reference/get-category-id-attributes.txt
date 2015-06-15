.. index:: GET /category/{id}/attributes
.. _get_category_id_attributes:

GET /category/{id}/attributes
=============================

**Required Scope:** ``api_ro`` or ``console_ro``

This URL returns the known :ref:`category_attributes` for the given category.

Only categories which have ``canPlaceAds`` set to ``true`` have attributes.
For all others an empty list will be returned.

.. warning::

	This call is deprecated and will be removed after September 2015.  It is
	only compatible with :ref:`categories_v1` and must only be used with the
	other :ref:`categories_v1_compatible_endpoints`. Otherwise, the attributes
	may not be recognized or editable.


Parameters
----------

=============    ========    ============================================================================
Name             Type        Description
=============    ========    ============================================================================
_include         string      Comma-separated-list of fields to include. Optional, default is all fields.
_exclude         string      Comma-separated-list of fields to omit. Optional, default empty.
=============    ========    ============================================================================

Errors
------

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
id                      2001    invalid argument            not a valid number
====================    ====    =======================     ==============================================================================

Example
-------

.. include:: ../examples/get-category-id-attributes-example.rst