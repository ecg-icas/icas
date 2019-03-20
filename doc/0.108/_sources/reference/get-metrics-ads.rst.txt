.. index:: GET /metrics/ads
.. _get_metrics_ads:

GET /metrics/ads
=======================

.. warning:: This is an **experimental** endpoint and not officially supported yet!

.. list-table::
 :widths: 20 80

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/vnd.ms-excel`` or ``text/csv``

This URL returns an ads performance report either in Excel or in CSV format depending on the
``Accept`` header. The report represents a timeseries breakdown of the performance of each ad which
has had performance-related activity in the requested period.

If the ``Accept`` header is ``application/vnd.ms-excel`` an Excel document is created.
If the ``Accept`` header is ``text/csv`` a `CSV <http://en.wikipedia.org/wiki/Comma-separated_values>`_ document is created.
Fields with a comma, fields with a quote or newline, and fields which start with a space will be enclosed in quotes.
Empty strings are not enclosed in quotes.

All dates and times are in the tenant timezone.


Parameters
~~~~~~~~~~

==============  ======  ==================  ======================================================================================================================================================================================================================================================================================================
Name             Type    Mandatory           Description
==============  ======  ==================  ======================================================================================================================================================================================================================================================================================================
aggregate       string  no                  Granularity of the timeseries breakdown. Possible values are: `hourly`, `daily`, `weekly`, `monthly`, and `yearly`. If not provided, aggregation granularity will be decided depending on the number of days in the requested interval. The larger the interval, the coarser the granularity of date.
startDate       string  yes                 Start date of the report in yyyy-MM-dd format
endDate         string  yes                 End date of the report in yyyy-MM-dd format (inclusive)
includeDeleted  bool    no                  Deleted ads are included/excluded. Default `false`
query           string   no                 Search phrase to filter on ad titles
==============  ======  ==================  ======================================================================================================================================================================================================================================================================================================

Report Columns
~~~~~~~~~~~~~~

Both excel and csv contain the following columns: (TBW)

===================      ==========================================================================
Name                     Description
===================      ==========================================================================
Date (Aggregated)        Date of the report row, grouped hourly, daily, weekly, monthly, or yearly
Ad id                    Id of the ad
L1 Category              Level 1 category name
L2 Category              Level 2 category name
L3 Category              Level 3 category name if it exists
Title                    Ad title
Start Date               The creation date of the ad
End Date                 If the ad is deleted, deletion date of the ad
Cpc                      Cpc of the ad for which performance metrics are calculated
Total spent              Total amount spent for this ad
Clicks                   Number of clicks that the ad received
Impressions              Number of impressions that the ad received
CTR                      Click through rate in %
URL clicks               Number of URL clicks that the ad received
Emails                   Number of email events that the ad received
Engagement CTR           Engagement conversion rate in %. Currently = (URL clicks + Emails)/Clicks
Region                   Region of the ad
Vendor id                Vendor id of the ad
===================      ==========================================================================


Examples
~~~~~~~~

.. include:: ../examples/get-metrics-ads-examples.rst


