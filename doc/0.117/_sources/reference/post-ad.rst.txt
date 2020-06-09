.. index:: POST /ad
.. _post_ad:

POST |an|/ad
============
.. |an| unicode:: 0x20 .. Workaround for ad blocker: apparently it blocks a section with id 'post-ad'

:ref:`post_ad_v3` | :ref:`post_ad_v2`

.. _post_ad_v3:

POST /ad v3
-----------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.ad-v3+json, application/json``

 * - Content-Type
   - ``application/sellside.ad-v3+json; charset=utf-8``


Version 3 works just like :ref:`post_ad_v2`, except the response body contains an additional field **statusReasons**.
This field is currently used to indicate the reason why a certain ad might be set to a certain status by our system.
This could be due to, for example, an action (like new website domain approval) pending from the user, which is a mechanism used to prevent account takeovers from setting the website URL to a malicious one.


Example
-------

.. include:: ../examples/post-ad-v3-example.rst


.. _post_ad_v2:

POST /ad v2
-----------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.ad-v2+json, application/json``

 * - Content-Type
   - ``application/sellside.ad-v2+json; charset=utf-8``

This URL creates a new ad for the current user.

If the ad was successfully
created then a **201 Created** is returned and the **Location** header
contains the URL to the newly created ad. The **optional** query parameter
**_body** with value **true** or **false** can be used to influence
whether the response body contains the ad in the body (or not) in case of success.
By default, this value is **true**. If the ad contains errors then the
server returns **400 Bad Request** with a list of errors.

For a new ad the **id** attribute must be omitted or set to zero. The
**title** and **description** must be set and will be trimmed. The
**salutation** contains either **MALE**, **FEMALE**, **COMPANY** or
**FAMILY**. The **sellerName** contains the name of the seller as displayed on
the site.

The **categoryId** must be an existing category id from a category which has
**canPlaceAds** set to **true**. If the **status** of the ad is **ACTIVE** and
the current number of active ads for the same user in this category exceeds
**maxNumberOfActiveAds** as defined in the category then an error is returned.
Ads with **status** equals to **PAUSED** do not have this restriction.

The **currency** must be set to **EUR** and all price amounts must be
specified in euro cents.

The **priceType** must be one of the valid types listed in :doc:`price-types`.
If the **priceType** is either **FIXED_PRICE** or **BIDDING_FROM** then a
**price** in the interval of ``(0,10000000000]`` must be specified. For all
other price types **price** must be omitted.

A new ad must have a **status** which can be either *ACTIVE* or *PAUSED*. An
active ad is shown on the site whereas a paused ad is not. See
:doc:`ad-status` for the list of valid ad status values.

The **cpc** is a mandatory field whose value depends on
the category. The **totalbudget** and **dailyBudget** are optional fields whose value
depend on the category. Omitting them will remove budget limits for this ad.
The category configuration which can be retrieved
through the category URL contains the valid bounds for these fields once filled in.

All prices are specified as numbers, i.e. a price of *10,50 EUR* must be
specified as *1050*. This applies to **price**, **cpc**, **totalBudget** and
**dailyBudget**.

The **postCode** is optional. In case it is not specified, its value is set to
**Heel Nederland**.

The **images** field is optional and can contain a list of up to 8
:ref:`ad_image_objects` which contain either the URL of the image
or a unique identifier provided by :ref:`post_image`.

The **attributes** field is optional and can contain a list of
:ref:`user_defined_attributes`.

The **originalPrice** field is optional, and will only be usable by enabled sellers.
If a seller is not enabled, but will use this field, an error will be thrown.

.. _post_ad_example:

Parameters
----------

====================    ========    ========    ================================================================================
Name                    Type        Default     Description
====================    ========    ========    ================================================================================
_body                   boolean     true        Include the created ad in the response body on success. Disabling this will speed up the call.
_include                string      ""          Comma-separated-list of fields to include.
_exclude                string      ""          Comma-separated-list of fields to omit.
_validate               boolean     false       Validate the request without executing it.
====================    ========    ========    ================================================================================

.. _post_ad_errors:

Errors
------

.. include:: post-ad-errors.rst

Example
-------

.. include:: ../examples/post-ad-v2-example.rst


