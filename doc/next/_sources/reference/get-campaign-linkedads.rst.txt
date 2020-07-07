.. index:: GET /campaign/{id}/linkedAds
.. _get_campaign_linkedads:

GET /campaign/{id}/linkedAds
============================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.campaign.linkedad-list-v1+json``


Returns the linkedAds of the specified campaign. A linkedAd (:ref:`Campaign Linked Ads <campaign-linked-ads>`) is the reference of an ad in a campaign, with possible overrides.
A single linkedAd has the following response model structure:

.. include:: ../examples/campaign-ad-response.rst


The status of the linkedAd cannot be set by the user; it is always ACTIVE.

If the campaign is in DELETED status, `404 Not Found` is returned.
If there are no linkedAds, an empty list is returned.

Parameters
~~~~~~~~~~

===============  ============     ============================================================================
Name             Type             Description
===============  ============     ============================================================================
limit            int              Limits the number of records returned. Default **and** maximum is 100.
offset           int              Skips the first N records.
adIds            string           List of ad id's to filter by
===============  ============     ============================================================================


Example:
--------

.. include:: ../examples/get-campaign-linkedads-example.rst
.. include:: ../examples/get-campaign-linkedads-example-2.rst

