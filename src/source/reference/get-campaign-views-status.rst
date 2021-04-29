.. index:: GET /campaign/{id}/views/status
.. _get_campaign_views/status:

GET /campaign/{id}/views/status
===============================
.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.ad-lite.list-v1+json``

Returns an overview of ``adLite`` objects, based on matching query parameters, in the context of a particular campaign. In addition, it returns the total size of the
result set matching the parameters criteria, and a next page token if additional pages are available.
This view should be used to quickly get insight on the status of ads in a campaign. It should not be used for scrapping the entire inventory of ads from that campaign.
At the moment ``adLite`` records are comprised of only the ad identifiers (sorted in descending order, newest ads first), however, we plan to enhance the response with more denormalized data pertaining an ad, based on further understanding of how this endpoint will be used.

Parameters
~~~~~~~~~~

===============  ============     ============================================================================
Name             Type             Description
===============  ============     ============================================================================
limit            int              Limits the number of adLite records returned. Default **and** maximum is 100.
categoryIds      list of ints     Comma-separated list of category id's to filter by. Only leaf category id's are useful, since ads can only be placed in leaf categories.
regionIds        list of ints     Comma-separated list of region id's to filter by.
pageToken        string           Skips the first N adLite records.
type             string           The type of status view to show. Possible values are: ``all``, ``active``, ``inactive``, ``archived``. Default value is ``all``. Only a single type can be provided.
===============  ============     ============================================================================

View Type
~~~~~~~~~

===================   ===================================================================================================================================================
Value                 Description
===================   ===================================================================================================================================================
all                   Default. Will not do any filtering, except for archived ads, which are excluded.
active                Ads that the seller intends to have actively running. Some ads may not be currently running because of budget or content related issues.
inactive              Ads that the seller has intentionally paused. Archived ads are excluded.
archived              Ads that the seller has intentionally archived. These ads cannot be reactivated.
===================   ===================================================================================================================================================

Example
-------

.. include:: ../examples/get-campaign-views-status-v1-example.rst


Errors
~~~~~~
.. include:: ../examples/get-campaign-views-status-v1-example-errors.rst
