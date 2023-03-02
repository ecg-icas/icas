.. index:: PUT /ad/{id}/status/{status}
.. _put_ad_id_status:

PUT /ad/{id}/status/{status}
============================

:ref:`put_ad_status_v5` | :ref:`put_ad_status`

.. _put_ad_status_v5:

PUT /ad/{id}/status/{status} v5:
--------------------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.ad-v5+json, application/json``

:ref:`put_ad_status_v5` introduces an accept header. See :ref:`ad_status_overview` for details on statuses.

Example
"""""""

.. include:: ../examples/put-ad-status-v5-example.rst

.. _put_ad_status:

PUT /ad/{id}/status/{status} without version
--------------------------------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/json``

This URL updates the status of the ad with the given ``id``. If the ad does
not exist or does not belong to the user the server returns **404 Not Found**.
If the ``id`` is invalid, i.e. not a positive integer the server returns **400
Bad Request**.

To set the new status append it to the base url. The status can be one of the
user controlled status values as defined in :doc:`ad-status`.

Changing the status to **ACTIVE** also changes the number of active
ads in this category for this user. If the current number of active ads
for this user in this category exceeds ``maxNumberOfActiveAds`` as defined
in the category then an error is returned. Setting a different status
than **ACTIVE** is always allowed.

If an ad has is in status **PAUSED** and also has no daily budget or total budget
remaining, this call will succeed. The resulting status of the ad will be either
:ref:`ad_status_budget_reached` or :ref:`ad_status_daily_budget_reached`,
depending on which budget has run out. In this case the ad will go live as soon
as budget is added.


Parameters
----------

====================    ========    ========    ================================================================================
Name                    Type        Default     Description
====================    ========    ========    ================================================================================
_validate               boolean     false       Validate the request without executing it.
====================    ========    ========    ================================================================================

Errors
------

====================    ====    ============================    ==============================================================================
Field                   Code    Error message                   Description
====================    ====    ============================    ==============================================================================
id                      2001    invalid argument                not a valid number
status                  2001    invalid argument                must be either *ACTIVE*, *PAUSED* or *DELETED*
status                  2017    ad status change not allowed    changing the status of the ad to the provided status is not allowed
====================    ====    ============================    ==============================================================================

Example
"""""""

.. code-block:: javascript

    PUT /ad/42/status/PAUSED
