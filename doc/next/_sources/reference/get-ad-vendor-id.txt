.. index:: GET /ad/byVendor/{vendorId}

.. _get_ad_vendor_id:

GET /ad/byVendor/{vendorId}
===========================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.ad-v2+json, application/json``

This URL returns a single ad with the given ``vendorId``.

If the ad does not exist or does not belong to the user the server returns
**404 Not Found**. If the ``vendorId`` is bigger than 64 characters the
server returns **400 Bad Request**.

.. warning::

	This call is only compatible with :ref:`categories_v2` and must only
	be used with the other :ref:`categories_v2_compatible_endpoints`. Otherwise,
	the attributes may not be recognized or editable.

.. note::

    The fields :ref:`ad_pageNumber` and :ref:`ad_suggestedCpcForPageOne` are
    currently expensive to compute. If you do not need their values consider
    excluding them to speed up the response. To exclude the fields add the
    following parameter to the request URL. ::

        ?_exclude=pageNumber,suggestedCpcForPageOne

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
vendorId                2005    value too long              max. length is 64 characters
====================    ====    =======================     ==============================================================================

Example
-------

.. include:: ../examples/get-ad-id-v2-example.rst

