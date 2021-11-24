.. index:: GET /metrics/report
.. _get_metrics_report:

GET /metrics/report
=======================

V2
~~~

V2 replaces the columns (``cpc``, ``totalSpent``,  ``dailyLimit``, ``totalBudget``, ``eCPC``) with their corresponding ``bidMicros``, ``spentMicros``, ``dailyBudgetMicros``, ``totalBudgetMicros``, ``eSpentMicros`` shown in micros unit.

.. list-table::
 :widths: 30 70

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/sellside.metrics.ad-hit-v2+json`` or ``application/sellside.metrics.ad-session-v2+json``

Returns a performance report for a selected date period, per ad.
The report contains statistics for performance events like impressions, clicks, url clicks, emails for all ads **which have had performance-related activity**.

The ``Accept`` header depends on the choice of the scope for the metrics. A scope for a metric defines the level at which that metric is defined — hit, session, or user.
Conceptually, user is the highest level scope and hit is the lowest level scope. For example, ``clicks`` counts the number of clicks that ad received when the scope is `hit`,
whereas it counts the number of sessions with clicks when the scope is `session`.

We plan to extend support for user-level scoped metrics if there is demand for it.



Parameters
----------

=======================     ========================    ========    ===========================
Field                       Example                     Type        Info
=======================     ========================    ========    ===========================
startDate                   "2014-11-24"                string      Report start date
endDate                     "2014-11-24"                string      Report end date (inclusive)
adIds                       "1,2,3"                     string      Comma-separated-list of ad id's which to filter the result set on. Optional, default empty to include data for all ads.
status                      "ACTIVE,DELETED"            string      Comma-separated-list of ad statuses which to filter the result set on. Optional, default is ACTIVE.
=======================     ========================    ========    ===========================

Fields
------

=======================     ========================    ========    =============================================================
Field                       Example                     Type        Info
=======================     ========================    ========    =============================================================
createDate                  "2014-12-05T16:12:53Z"      dateTime    The date/time this report call got requested (in UTC ISO8601 format)
startDate                   "2014-11-23"                string      The start of the period this report covers. Tenant time zone is assumed.
endDate                     "2014-11-24"                string      The end of the period this report covers. Tenant time zone is assumed.
data                        see below                   array       The report data; each element in this array represents the data for an ad.
=======================     ========================    ========    =============================================================



Data contents
-------------

=======================     ========================    ========   ========   =============================================================
Field                       Example                     Type       Version    Info
=======================     ========================    ========   ========   =============================================================
adId                        1                           long       V1, V2     Id of the ad to which the report row belongs to.
bidMicros                   50000                       int        V2         Bid Micros of the ad (in micros).
cpc                         5                           int        V1         CPC of the ad (in cents).
impressions                 40                          long       V1, V2     Number of impressions this ad received.
clicks                      10                          long       V1, V2     Number of clicks this ad received.
urlClicks                   3                           int        V1, V2     Number of url clicks this ad received.
emails                      2                           int        V1, V2     Number of email requests this ad received.
engagement                  5                           int        V1, V2     Number of engagements this ad received. Depending on the tenant, this could be the same as urlClicks, or a summation of several metrics.
spentMicros                 5000                        long       V2         Total amount spent for this ad (in micros).
totalSpent                  2000                        long       V1         Total amount spent for this ad (in cents).
ctr                         0.75                        float      V1, V2     Click-through rate of the ad.
engagementCTR               0.7                         float      V1, V2     Number of engagements leads from clicks this ad received.
websiteCTR                  0.7                         float      V1, V2     Number of website leads from clicks this ad received.
startDate                   "2012-08-31T16:12:53Z"      date       V1, V2     Creation date of the ad.
endDate                     "2012-08-31T16:12:53Z"      date       V1, V2     Deletion date of the ad if the ad is deleted, null otherwise.
title                       "Brother Fax voor 99,99"    string     V1, V2     Title of the ad.
categoryId                  631                         int        V1, V2     Category id of the ad.
vendorId                    "vndr"                      string     V1, V2     Vendor id of the ad.
dailyBudgetMicros           3000                        long       V2         Daily limit of the ad (in micros).
dailyLimit                  2000                        long       V1         Daily limit of the ad (in cents).
totalBudgetMicros           7000                        long       V2         Total budget of the ad (in micros).
totalBudget                 5000                        long       V1         Total budget of the ad (in cents).
relativePerformance         75                          int        V1, V2     Returns the relative performance of the ad (on a scale of [1-100]) compared to competition within the ad's category. Higher score means better performance. A score of 0 could indicate there is not enough data to infer the value at the moment.
eSpentMicros                0.42                        float      V2         Returns the effective cost per website click in micros
eCPC                        0.42                        float      V1         Returns the eCPC (effective cost per website click) in cents
=======================     ========================    ========   ========   =============================================================


V1
~~~

.. list-table::
 :widths: 30 70

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/sellside.metrics.ad-hit-v1+json`` or ``application/sellside.metrics.ad-session-v1+json``




Example
-------
.. include:: ../examples/get-metrics-report-example-v2.rst

.. include:: ../examples/get-metrics-report-example.rst
