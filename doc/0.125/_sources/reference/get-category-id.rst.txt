.. index:: GET /category/{id}
.. _get_category_id:

GET /category/{id}
==================

:ref:`get_category_id_v5` | :ref:`get_category_id_v2`

This URL returns the category tree or parts of it in the format described in
:ref:`categories` starting from the category with the given category
``id``. To return the category tree starting from the root node use id ``0``.
If the category does not exist the server returns **404 Not Found**. If the
``id`` is invalid, i.e. not a positive integer the server returns **400 Bad
Request**.

The ``levels`` parameter specifies how many levels starting from
the current one you want to retrieve. The default is 0 which means that only
the category itself is returned. To retrieve all sub levels specify a
sufficiently large number, e.g. 9999.


.. _get_category_id_v5:

GET /category/{id} v5
---------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.category-v5+json, application/json``

Example
"""""""

.. include:: ../examples/get-category-id-v5-example.rst

.. _get_category_id_v2:

GET /category/{id} v2
---------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.category-v2+json, application/json``


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
"""""""

.. include:: ../examples/get-category-id-v2-example.rst
