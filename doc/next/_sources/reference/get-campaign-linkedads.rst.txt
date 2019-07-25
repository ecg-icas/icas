.. index:: GET /campaign/{id}/linkedAds
.. _get_campaign_linkedads:

GET /campaign/{id}/linkedAds
============================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.campaign-linkedads-list-v1+json``


This endpoint will return the linkedAds of the specified campaign. A linkedAd is the reference of an ad in a campaign, with possible overrides.
A single linkedAd has the following model structure:

.. include:: ../examples/campaign-ad-response.rst


The status of the linkedAd cannot be set by the user; it is always ACTIVE.


Example:
--------

.. include:: ../examples/get-campaign-linkedads-example.rst

