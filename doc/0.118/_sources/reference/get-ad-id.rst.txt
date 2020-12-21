.. index:: GET /ad/{id}

.. _get_ad_id:

GET /ad/{id}
============

:ref:`get_ad_id_v3` | :ref:`get_ad_id_v2`

.. _get_ad_id_v3:

GET /ad/{id} v3
---------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.ad-v3+json, application/json``

Version 3 works just like :ref:`get_ad_id_v2`, except the response body contains an additional field **statusReasons**.
This field is currently used to indicate the reason why a certain ad might be set to a certain status by our system.
This could be due to, for example, an action (like new website domain approval) pending from the user, which is a mechanism used to prevent account takeovers from setting the website URL to a malicious one.

Example
-------

.. include:: ../examples/get-ad-id-v3-example.rst


.. _get_ad_id_v2:

GET /ad/{id} v2
---------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.ad-v2+json, application/json``

This URL returns a single ad with the given ``id``.

If the ad does not exist or does not belong to the user the server returns
**404 Not Found**. If the ``id`` is invalid, i.e. not a positive integer the
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
id                      2001    invalid argument            not a valid number
id                      1006    type mismatch               the provided value for the field was not of the correct type
====================    ====    =======================     ==============================================================================

Example
-------

.. include:: ../examples/get-ad-id-v2-example.rst


