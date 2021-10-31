.. index:: GET /metrics/report
.. _get_metrics_report:

GET /metrics/report
=======================

V2
~~~

.. list-table::
 :widths: 30 70

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/sellside.metrics.ad-hit-v2+json`` or ``application/sellside.metrics.ad-session-v2+json``


V1
~~~

.. list-table::
 :widths: 30 70

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/sellside.metrics.ad-hit-v1+json`` or ``application/sellside.metrics.ad-session-v1+json``

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

V2
~~~

=======================     ========================    ========    =============================================================
Field                       Example                     Type        Info
=======================     ========================    ========    =============================================================
adId                        1                           long        Id of the ad to which the report row belongs to.
bidMicros                   50000                       int         Bid Micros of the ad (in micros).
impressions                 40                          long        Number of impressions this ad received.
clicks                      10                          long        Number of clicks this ad received.
urlClicks                   3                           int         Number of url clicks this ad received.
emails                      2                           int         Number of email requests this ad received.
engagement                  5                           int         Number of engagements this ad received. Depending on the tenant, this could be the same as urlClicks, or a summation of several metrics.
spentMicros                 5000                        long        Total amount spent for this ad (in micros).
ctr                         0.75                        float       Click-through rate of the ad.
engagementCTR               0.7                         float       Number of engagements leads from clicks this ad received.
websiteCTR                  0.7                         float       Number of website leads from clicks this ad received.
startDate                   "2012-08-31T16:12:53Z"      date        Creation date of the ad.
endDate                     "2012-08-31T16:12:53Z"      date        Deletion date of the ad if the ad is deleted, null otherwise.
title                       "Brother Fax voor 99,99"    string      Title of the ad.
categoryId                  631                         int         Category id of the ad.
vendorId                    "vndr"                      string      Vendor id of the ad.
dailyBudgetMicros           3000                        long        Daily limit of the ad (in micros).
totalBudgetMicros           7000                        long        Total budget of the ad (in micros).
relativePerformance         75                          int         Returns the relative performance of the ad (on a scale of [1-100]) compared to competition within the ad's category. Higher score means better performance. A score of 0 could indicate there is not enough data to infer the value at the moment.
eSpentMicros                0.42                        float       Returns the eCPC (effective cost per website click) in micros
=======================     ========================    ========    =============================================================

V1
~~~

=======================     ========================    ========    =============================================================
Field                       Example                     Type        Info
=======================     ========================    ========    =============================================================
adId                        1                           long        Id of the ad to which the report row belongs to.
cpc                         5                           int         CPC of the ad (in cents).
impressions                 40                          long        Number of impressions this ad received.
clicks                      10                          long        Number of clicks this ad received.
urlClicks                   3                           int         Number of url clicks this ad received.
emails                      2                           int         Number of email requests this ad received.
engagement                  5                           int         Number of engagements this ad received. Depending on the tenant, this could be the same as urlClicks, or a summation of several metrics.
totalSpent                  2000                        long        Total amount spent for this ad (in cents).
ctr                         0.75                        float       Click-through rate of the ad.
engagementCTR               0.7                         float       Number of engagements leads from clicks this ad received.
websiteCTR                  0.7                         float       Number of website leads from clicks this ad received.
startDate                   "2012-08-31T16:12:53Z"      date        Creation date of the ad.
endDate                     "2012-08-31T16:12:53Z"      date        Deletion date of the ad if the ad is deleted, null otherwise.
title                       "Brother Fax voor 99,99"    string      Title of the ad.
categoryId                  631                         int         Category id of the ad.
vendorId                    "vndr"                      string      Vendor id of the ad.
dailyLimit                  2000                        long        Daily limit of the ad (in cents).
totalBudget                 5000                        long        Total budget of the ad (in cents).
relativePerformance         75                          int         Returns the relative performance of the ad (on a scale of [1-100]) compared to competition within the ad's category. Higher score means better performance. A score of 0 could indicate there is not enough data to infer the value at the moment.
eCPC                        0.42                        float       Returns the eCPC (effective cost per website click) in cents
=======================     ========================    ========    =============================================================

Example
-------
.. include:: ../examples/get-metrics-report-example-v2.rst

.. include:: ../examples/get-metrics-report-example.rst
