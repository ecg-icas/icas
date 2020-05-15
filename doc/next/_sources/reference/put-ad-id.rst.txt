.. index:: PUT /ad/{id}
.. _put_ad_id:

PUT /ad/{id}
============

:ref:`put_ad_id_v3` | :ref:`put_ad_id_v2` | :ref:`put_ad_id_v1`

.. _put_ad_id_v3:

PUT /ad/{id} v3
---------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.ad-v3+json, application/json``

 * - Content-Type
   - ``application/sellside.ad-v3+json; charset=utf-8``


Version 3 works just like :ref:`put_ad_v2`, except the response body may contain an additional field **statusReasons**.
This field is currently used to indicate the reason why a certain ad might be set to a certain status by our system.
This could be due to, for example, an action (like new website domain approval) pending from the user, which is a mechanism used to prevent account takeovers from setting the website URL to a malicious one.

Example
-------

.. include:: ../examples/put-ad-v3-example.rst


.. _put_ad_id_v2:

PUT /ad/{id} v2
---------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.ad-v2+json, application/json``

 * - Content-Type
   - ``application/sellside.ad-v2+json; charset=utf-8``

This URL updates the ad with the given ``id``.

.. warning::

    This call is only compatible with :ref:`categories_v2` and must only
    be used with the other :ref:`categories_v2_compatible_endpoints`. Otherwise,
    the attributes may not be recognized or editable.

If the ad was successfully updated then a **200 OK** is returned. The
**optional** query parameter ``_body`` with value ``true`` or ``false`` can be
used to influence whether the response body contains the ad in the body (or
not) in case of success. By default, this value is ``true``. If the ad does not
exist or does not belong to the user the server returns **404 Not Found**. If
the ``id`` is invalid, i.e. not a positive integer the server returns **400
Bad Request**.

.. note::

    Updating deleted ads is not allowed and will result in a **400 Bad Request**.

All writeable fields listed in :ref:`ad-fields` can be changed. Attempting to
change a non-writeable field results in a **400 Bad Request**

All validation rules for creating an ad apply exactly the same.

Additionally, the following rules apply:

The :ref:`ad_totalBudget` cannot be lower than the minimum budget as
defined in the category and also cannot be lower than the sum of :ref:`ad_cpc` and
the current value of :ref:`ad_spentBudget`. Similarly, the :ref:`ad_dailyBudget`
cannot be lower than than the minimum daily budget as defined in the category and
also cannot be lower than the sum of :ref:`ad_cpc` and the current value of
**dailySpent**.

.. note::

    The value of **dailySpent** is not exposed via the API.

.. note::

    The fields :ref:`ad_pageNumber` and :ref:`ad_suggestedCpcForPageOne` are
    currently expensive to compute. If you do not need their values consider
    excluding them to speed up the response. To exclude the fields add the
    following parameter to the request URL. ::

        ?_exclude=pageNumber,suggestedCpcForPageOne

.. _put_ad_id_example:

Parameters
----------

====================    ========    ========    ================================================================================
Name                    Type        Default     Description
====================    ========    ========    ================================================================================
_body                   boolean     true        Include the modified ad in the response body on success. Disabling this will speed up the call. Setting this to false will override any _include or _exclude.
_include                string      ""          Comma-separated-list of fields to include.
_exclude                string      ""          Comma-separated-list of fields to omit.
_validate               boolean     false       Validate the request without executing it.
====================    ========    ========    ================================================================================


Errors
------

Additional error codes for PUT /ad/{id}.

====================    ====    ============================    ==========================================================================================
Field                   Code    Error message                   Description
====================    ====    ============================    ==========================================================================================
status                  2001    invalid argument                must be either *ACTIVE*, *PAUSED* or *DELETED*
totalBudget             2002    out of range                    totalBudget is not within max(category.minBudget, ad.spentBudget) and category.maxBudget
categoryId              2012    category change not allowed     Changing the category of an ad is not allowed
status                  2017    ad status change not allowed    Changing the status of an ad is not allowed
totalBudget             2019    insufficient budget             Budget for ad is insufficient
dailyBudget             2020    insufficient daily budget       Daily budget for ad is insufficient
categoryId              2023    category deleted                The category has been deleted and will not allow creation/updating of ads
====================    ====    ============================    ==========================================================================================

.. note::

    It is _not_ allowed to edit deleted ads (**DELETED** or **DELETED_BY_CS** status).

Error codes for POST /ad.

.. include:: post-ad-errors.rst

Example
-------

.. include:: ../examples/put-ad-v2-example.rst

.. _put_ad_id_v1:

PUT /ad/{id} v1
---------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.ad-v1+json, application/json``

 * - Content-Type
   - ``application/sellside.ad-v1+json; charset=utf-8``

Version 1 works just like :ref:`put_ad_id_v2` except that it is compatible
with :ref:`categories_v1`.

.. warning::

    This call is deprecated and will be removed after September 2015.  It is
    only compatible with :ref:`categories_v1` and must only be used with the
    other :ref:`categories_v1_compatible_endpoints`. Otherwise, the attributes
    may not be recognized or editable.

Example
-------

.. include:: ../examples/put-ad-v1-example.rst

