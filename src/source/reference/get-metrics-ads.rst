.. index:: GET /metrics/ads
.. _get_metrics_ads:

GET /metrics/ads
=================

.. include:: ../bidding-micros.rst

V2
~~

V2 replaces two columns (``spent``, ``cpc``) that used to be in the tenant local currency (EUR, $) with
their corresponding ``spentMicros`` and ``bidMicros`` shown in micros unit.


.. list-table::
 :widths: 30 70

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/vnd.ms-excel;v=2`` or ``text/csv;v=2``

 * - Accept-Language
   - preferred locale (e.g., ``nl-NL``, ``fr-BE``, ``en-CA``)


This URL returns an ads performance report either in Excel or in CSV format depending on the
``Accept`` header. The report represents a timeseries breakdown of the performance of each ad which
**has had performance-related activity** in the requested period.

If the ``Accept`` header is ``application/vnd.ms-excel;v=2`` an Excel document is created, in ``.xlsx`` format.

If the ``Accept`` header is ``text/csv;v=2`` a `CSV <http://en.wikipedia.org/wiki/Comma-separated_values>`_ document is created, in the standard `RFC-4180 <https://tools.ietf.org/html/rfc4180>`_ format.
**Fields with a comma, fields with a quote or newline, and fields which start with a space will be enclosed in quotes.
Empty strings are not enclosed in quotes.**


All dates and times are in the tenant timezone.

The ``Accept-Language`` header advertises the preferred client locales (language and region) for the report column names. Both ``language_REGION`` and ``language-REGION`` are supported formats, and can be assigned optional weights. If the preferred locale(s) are not available, a default one is used. Currently available locales are tenant-specific, and are listed below:

==============  =======================
Tenant           Locales
==============  =======================
Marktplaats       ``nl_NL``
2dehands          ``nl_BE``, ``fr_BE``
Kijiji            ``en_CA``, ``fr_CA``
==============  =======================

Parameters
~~~~~~~~~~

==============  ================  ==================  ======================================================================================================================================================================================================================================================================================================
Name             Type                Mandatory           Description
==============  ================  ==================  ======================================================================================================================================================================================================================================================================================================
aggregate       string               no                 Granularity of the timeseries breakdown. Possible values are: ``daily``, ``weekly``, ``monthly``, and ``yearly``. Default is ``daily``.
startDate       string               yes                Start date of the report in ``YYYY-MM-DD`` format (inclusive). Tenant timezone is assumed.
endDate         string               yes                End date of the report in ``YYYY-MM-DD`` (inclusive). Tenant timezone is assumed.
includeDeleted  bool                 no                 Deleted ads are included/excluded. Default is ``false``
query           string               no                 Search phrase to filter on ad titles
fields          list of strings      no                 Comma-separated list of column fields to include in the report. Possible values are listed in the ``Field`` column in the table below. By default all fields are included, and this may **affect the speed of data generation**.
==============  ================  ==================  ======================================================================================================================================================================================================================================================================================================


Report Columns
~~~~~~~~~~~~~~

Both the excel and the csv formats contain the following columns by default:

====================   =================   ========   ===============================================================
Name                   Field               Version    Description
====================   =================   ========   ===============================================================
Date (Aggregated)      ``date``            V1, V2     Date of the report row, grouped daily, weekly, monthly, or yearly. For daily and weekly aggregation the format is ``YYYY-MM-DD``, for monthly aggregation - ``YYYY-MM``, and for yearly - ``YYYY``. All dates are in tenant timezone.
Ad ID                  ``adID``            V1, V2     ID of the ad
L1 Category            ``L1Category``      V1, V2     Level 1 category name
L2 Category            ``L2Category``      V1, V2     Level 2 category name
L3 Category            ``L3Category``      V1, V2     Level 3 category name, if applicable
Title                  ``title``           V1, V2     Title of the ad
Start Date             ``startDate``       V1, V2     Creation date of the ad
End Date               ``endDate``         V1, V2     If the ad is deleted, deletion date of the ad
Bid (Micros)           ``bidMicros``       V2         Bid of the ad for which performance metrics are calculated, in micros unit
Total Spent (Micros)   ``spentMicros``     V2         Total amount spent for this ad, in micros unit
CPC                    ``CPC``             V1         CPC of the ad for which performance metrics are calculated, in local currency
Total spent            ``spent``           V1         Total amount spent for this ad, in Local Currency
Clicks                 ``clicks``          V1, V2     Number of clicks that the ad received
Impressions            ``impressions``     V1, V2     Number of impressions that the ad received
CTR                    ``viewCTR``         V1, V2     Click-through rate in %
URL clicks             ``websiteClicks``   V1, V2     Number of URL clicks that the ad received
Emails                 ``emails``          V1, V2     Number of email events that the ad received
Engagement CTR         ``engagementCTR``   V1, V2     Engagement conversion rate in %. Calculation: ``(URL clicks + Emails) / Clicks``
Region                 ``region``          V1, V2     Region name, of the ad
Vendor ID              ``vendorID``        V1, V2     Vendor ID of the ad
====================   =================   ========   ===============================================================



V1
~~
.. list-table::
 :widths: 30 70

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/vnd.ms-excel`` or ``text/csv``

 * - Accept-Language
   - preferred locale (e.g., ``nl-NL``, ``fr-BE``, ``en-CA``)


Examples
~~~~~~~~

.. include:: ../examples/get-metrics-ads-examples.rst


Errors
~~~~~~~~

.. include:: ../examples/get-metrics-ads-examples-errors.rst
