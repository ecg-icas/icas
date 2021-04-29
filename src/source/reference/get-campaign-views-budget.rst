.. index:: GET /campaign/{id}/views/budget
.. _get_campaign_views/budget:

GET /campaign/{id}/views/budget
===============================
.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.ad-lite.list-v1+json``

Returns an overview of ``adLite`` objects, based on matching query parameters, in the context of a particular campaign. In addition, it returns the total size of the
result set matching the parameters criteria, and a next page token if additional pages are available.
This view should be used to quickly get insight on the ads in a campaign that might need attention or optimizing, from an ad total budget perspective. It should not be used for scrapping the entire inventory of ads from that campaign.
At the moment ``adLite`` records are comprised of only the ad identifiers (by default sorted in descending order, newest ads first, unless specified otherwise), however, we plan to enhance the response with more denormalized data pertaining an ad, based on further understanding of how this endpoint will be used.

Parameters
~~~~~~~~~~

=====================  ============     ================================================================================================================================================================================================================================
Name                    Type             Description
=====================  ============     ================================================================================================================================================================================================================================
limit                  int               Limits the number of adLite records returned. Default **and** maximum is 100.
categoryIds            list of ints      Comma-separated list of category id's to filter by. Only leaf category id's are useful, since ads can only be placed in leaf categories.
regionIds              list of ints      Comma-separated list of region id's to filter by. RegionIds are not a concept used by all tenants, check before usage.
pageToken              string            Skips the first N adLite records.
remainingBudgetCents   int               Returns ads that have less-than, or equal, amount of cents of remaining total budget. By definition, it takes into account only ads that have set a total budget limit. Optional; no filtering applied if not provided.
outOfBudget            bool              Returns ads that are out of total budget. By definition, it takes into account only ads that have set a total budget limit. Optional; no filtering applied if not provided.
noLifetimeSpend        bool              Returns ads that have not had any spending activity in their lifetime. Optional; no filtering applied if not provided.
=====================  ============     ================================================================================================================================================================================================================================

Example
-------

.. include:: ../examples/get-campaign-views-budget-v1-example.rst


Errors
~~~~~~
.. include:: ../examples/get-campaign-views-budget-v1-example-errors.rst
