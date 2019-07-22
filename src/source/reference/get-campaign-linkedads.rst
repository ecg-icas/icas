.. index:: GET /campaign/{id}/linkedAds
.. _get_campaign_linkedads:

GET /campaign/{id}/linkedAds
============================

This endpoint will return the linkedAds of the specified campaign. A linkedAd is the reference of an ad in a campaign, with possible overrides.
A single linkedAd has the following fields:

========= ======== =================================================================================
Field     Type     Description
========= ======== =================================================================================
AdID      int      the ID of the Ad this linkedAd refers to
status    string   the current status of this linkedAd. One of `ACTIVE` or `BUDGET_REACHED`
cpc       int      instead of using the campaign's cpc, use this cpc
budgets   []budget Limit this listing's spent by these budgets too. Does not void campaign budgets.
========= ======== =================================================================================

The status of the linkedAd cannot be set by the user; it is always ACTIVE.


The format of the response is as below:

.. include:: ../examples/get-campaign-linkedads-example.rst

