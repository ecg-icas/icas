.. index:: GET /category/{id}
.. _get_category_id:

GET /category/{id}
==================

:ref:`get_category_id_v2` | :ref:`get_category_id_v1`

.. _get_category_id_v2:

GET /category/{id} v2
---------------------

**Required Scope:** ``api_ro`` or ``console_ro``

This URL returns the category tree or parts of it in the format described in
:ref:`categories_v2` starting from the category with the given category
``id``. To return the category tree starting from the root node use id ``0``.
If the category does not exist the server returns **404 Not Found**. If the
``id`` is invalid, i.e. not a positive integer the server returns **400 Bad
Request**.

The ``levels`` parameter specifies how many levels starting from
the current one you want to retrieve. The default is 0 which means that only
the category itself is returned. To retrieve all sub levels specify a
sufficiently large number, e.g. 9999.

.. note::

	The format is substantially different than the format used for
	:ref:`get_category_id_v1`. Since the attribute keys have changed you also
	need to use :ref:`get_ad_id_v2` and :ref:`get_ad_v3` instead of the older
	versions.


.. _get_category_id_v1:

GET /category/{id} v1
---------------------

**Required Scope:** ``api_ro`` or ``console_ro``

This URL returns the category tree or parts of it in the format described in
:ref:`categories_v1` starting from the node with the given category ``id``. To
return the category tree starting from the root node use id ``0``. If the
category does not exist the server returns **404 Not Found**. If the ``id`` is
invalid, i.e. not a positive integer the server returns **400 Bad Request**.

The ``levels`` parameter specifies how many levels starting from the current
one you want to retrieve. The default is 0 which means that only the current
level is being returned. To retrieve all sub levels specify a sufficiently
large number, e.g. 9999.

.. warning::

	This call is deprecated and will be removed after September 2015.  It is
	only compatible with :ref:`categories_v1` and must only be used with the
	other :ref:`categories_v1_compatible_endpoints`. Otherwise, the attributes
	may not be recognized or editable.

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
id                      2001    invalid argument            not a valid number
id                      2002    out of range                negative number
levels                  2001    invalid argument            not a valid number
levels                  2002    out of range                negative number
====================    ====    =======================     ==============================================================================

Example
-------

.. include:: ../examples/get-category-id-v1-example.rst