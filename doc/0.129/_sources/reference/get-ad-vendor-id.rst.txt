.. index:: GET /ad/byVendor/{vendorId}

.. _get_ad_vendor_id:

GET /ad/byVendor/{vendorId}
===========================

:ref:`get_ad_vendor_id_v5` | :ref:`get_ad_vendor_id_v2`

.. warning::

    :ref:`get_ad_vendor_id_v2` is now officially deprecated and scheduled for removal on May, 1st 2023. Please move to use :ref:`get_ad_vendor_id_v5`.

    :ref:`get_ad_vendor_id_v3` is now officially deprecated and scheduled for removal on May, 1st 2023. Please move to use :ref:`get_ad_vendor_id_v5`.

    :ref:`get_ad_vendor_id_v3` is now officially unused and removed on September, 1st 2024. Please move to use :ref:`get_ad_vendor_id_v5`.

.. _get_ad_vendor_id_v5:

GET /ad/byVendor/{vendorId} v5
------------------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.ad-v5+json, application/json``

This URL returns a single ad with the given ``vendorId``.

If the ad does not exist or does not belong to the user the server returns
**404 Not Found**. If the ``vendorId`` is bigger than 64 characters the
server returns **400 Bad Request**.

Example
"""""""

.. include:: ../examples/get-ad-vendorid-v5-example.rst

.. _get_ad_vendor_id_v2:

GET /ad/byVendor/{vendorId} v2
------------------------------

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
"""""""

.. include:: ../examples/get-ad-id-v2-by-vendor.rst
