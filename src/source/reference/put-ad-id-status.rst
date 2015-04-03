.. index:: PUT /ad/{id}/status
.. _put_ad_id_status:

PUT /ad/{id}/status
===================

:ref:`scopes` **write**

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
status                  2017    ad status change not allowed    changing the status of an ad is not allowed
totalBudget             2019    insufficient budget             Budget for ad is insufficient
dailyBudget             2020    insufficient daily budget       Daily budget for ad is insufficient
====================    ====    ============================    ==============================================================================

Example
-------

.. code-block :: http

    PUT /ad/42/status/PAUSED