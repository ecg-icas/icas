.. _ISO 8601: http://en.wikipedia.org/wiki/ISO_8601
.. index:: Campaigns
.. _campaigns:

Campaigns
=========

A Campaign is a group of ads, sharing a campaign budget. With campaigns, it is possible to control spending for this entire list of ads and,
in one go, start/stop advertising with the entire list of (active) ads.
Campaigns can have their own budgets, both daily and total.

For the time being, we only allow multiple campaigns for sellers of Kleinanzeigen. This means for all other markets,
we allow only 1 campaign per seller, effectively grouping *all* the ads in that one campaign.
To make transitions to use campaigns easier, we will ensure that each (new or existing) seller already has a campaign, and if the
seller has ads, these will be part of the campaign. 

The first campaign to be created, either explicitly or by us ensuring there is one, will also become the `default campaign`. This
means that whenever ads are created through API without specifying a campaign Id, the ad will become part of this `default campaign`.
For markets where only one campaign per seller is allowed at the moment, this campaign is also the default.

You can get your campaign by calling `GET /campaigns <https://ecg-icas.github.io/icas/openapi/index.html#/Campaigns/get_campaigns>`_ or `GET /campaign/{id} <https://ecg-icas.github.io/icas/openapi/index.html#/Campaigns/get_campaign__id_>`_. Campaign budgets can be modified by using
`PUT /campaign/{id}/budgets <https://ecg-icas.github.io/icas/openapi/index.html#/Campaigns/put_campaign__id__budgets>`_, and controlling campaign status can be done by `PUT /campaign/{id}/status/{status} <https://ecg-icas.github.io/icas/openapi/index.html#/Campaigns/put_campaign__id__status__status_>`_. We expect to
add more campaign functionality in the future.

Check our extensive :ref:`migration-guide` for more information on how to transition to using campaigns.