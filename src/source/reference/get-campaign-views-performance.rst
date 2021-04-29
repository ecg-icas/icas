.. index:: GET /campaign/{id}/views/performance
.. _get_campaign_views/performance:

GET /campaign/{id}/views/performance
====================================
.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.ad-lite.list-v1+json``

Returns an overview of ``adLite`` objects, based on matching query parameters, in the context of a particular campaign. In addition, it returns the total size of the
result set matching the parameters criteria.
This view should be used to quickly get insight on the ads in a campaign that might need attention or optimizing, from an ad performance perspective.

The performance view always operates on a particular requested date range (by default: the past 7 days), and has no pagination possibilities at the moment.
It should not be used for scrapping the entire inventory of ads from that campaign.
At the moment ``adLite`` records are comprised of only the ad identifiers, however, we plan to enhance the response with more denormalized data pertaining an ad, based on further understanding of how this endpoint will be used.

Parameters
~~~~~~~~~~

=====================  ============     ================================================================================================================================================================================================================================
Name                    Type             Description
=====================  ============     ================================================================================================================================================================================================================================
limit                  int               Limits the number of adLite records returned. Default **and** maximum is 100.
categoryIds            list of ints      Comma-separated list of category id's to filter by. Only leaf category id's are useful, since ads can only be placed in leaf categories.
regionIds              list of ints      Comma-separated list of region id's to filter by. RegionIds are not a concept used by all tenants, check before usage.
type                   string            Mandatory field, defines the type of performance view to show. The possible values are described below.
startDate              string            Start date by which to limit the performance view data. Format ``YYYY-MM-DD``` (inclusive). Default is today-7 days (in the tenant timezone).
endDate                string            End date by which to limit the performance view data. Format ``YYYY-MM-DD``` (inclusive). Default is today's date (in the tenant timezone).  Cannot be before ``startDate`` chronologically.
Scope                  string            The level at which the views are defined. Possible values are ``hit`` (default if not provided) and ``session``.
=====================  ============     ================================================================================================================================================================================================================================

At the ``hit`` scope level, each individual activity event, like click or impression, is counted as one, regardless if that came from the same device/user or not. At the ``session`` level, activity events coming from the same user session are counted as one.


View Type
~~~~~~~~~

===================   =======================================================================================================================================================================================
Value                 Description
===================   =======================================================================================================================================================================================
HighCtr               Default. Ads that have the highest CTR value in the selected date range. Ads without any traffic are not included.
LowCtr                Ads that have the lowest CTR value in the selected date range. Ads without any traffic are not included.
HighUrlCtr            Ads that have the highest URL CTR value in the selected date range. Ads without any traffic are not included.
LowUrlCtr             Ads that have the lowest URL CTR value in the selected date range. Ads without any traffic are not included.
HighUrlClicks         Ads that have the highest number of URL clicks in the selected date range. Ads without any traffic are not included.
HighClicks            Ads that have the highest number of clicks in the selected date range. Ads without any traffic are not included.
HighECpc              Ads that have the highest ECPC (effective Cost-Per-Click, or the click cost for a URL click) value in the selected date range. Ads without any traffic are not included.
LowECpc               Ads that have the lowest ECPC (effective Cost-Per-Click, or the click cost for a URL click) value in the selected date range. Ads without any traffic are not included.
HighSpend             Ads that have the highest spend in the selected date range. Ads without any traffic are not included.
===================   =======================================================================================================================================================================================

Example
-------

.. include:: ../examples/get-campaign-views-performance-v1-example.rst


Errors
~~~~~~
.. include:: ../examples/get-campaign-views-performance-v1-example-errors.rst
