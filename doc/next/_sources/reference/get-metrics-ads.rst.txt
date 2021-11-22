.. index:: GET /metrics/ads
.. _get_metrics_ads:

GET /metrics/ads
=================


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



V2
~~
.. list-table::
 :widths: 30 70

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/vnd.ms-excel;v=2`` or ``text/csv;v=2``

 * - Accept-Language
   - preferred locale (e.g., ``nl-NL``, ``fr-BE``, ``en-CA``)


V2 exposes the bidding concept, instead of static CPC we expose the Bid (in Micros). As a result discrepancy is expected between the Bid and the Total Spent column (the bid value used is not the same as the value that is charged). The bid and spent values are represented as Micros instead of the local currency used in V1. One micro (as the name suggests) is equal to 1M local currency units.


This URL returns an ads performance report either in Excel or in CSV format depending on the
``Accept`` header. The report represents a timeseries breakdown of the performance of each ad which
**has had performance-related activity** in the requested period.

If the ``Accept`` header is ``application/vnd.ms-excel`` an Excel document is created, in ``.xlsx`` format.

If the ``Accept`` header is ``text/csv`` a `CSV <http://en.wikipedia.org/wiki/Comma-separated_values>`_ document is created, in the standard `RFC-4180 <https://tools.ietf.org/html/rfc4180>`_ format.
**Fields with a comma, fields with a quote or newline, and fields which start with a space will be enclosed in quotes.
Empty strings are not enclosed in quotes.**

All dates and times are in the tenant timezone.

The ``Accept-Language`` header advertises the preferred client locales (language and region) for the report column names. Both ``language_REGION`` and ``language-REGION`` are supported formats, and can be assigned optional weights. If the preferred locale(s) are not available, a default one is used. Currently available locales are tenant-specific, and are listed below:


Report Columns V2
~~~~~~~~~~~~~~~~~

Both the excel and the csv formats contain the following columns by default:

====================   =================   ===============================================================
Name                   Field               Description
====================   =================   ===============================================================
Date (Aggregated)      ``date``            Date of the report row, grouped daily, weekly, monthly, or yearly. For daily and weekly aggregation the format is ``YYYY-MM-DD``, for monthly aggregation - ``YYYY-MM``, and for yearly - ``YYYY``. All dates are in tenant timezone.
Ad ID                  ``adID``            ID of the ad
L1 Category            ``L1Category``      Level 1 category name
L2 Category            ``L2Category``      Level 2 category name
L3 Category            ``L3Category``      Level 3 category name, if applicable
Title                  ``title``           Title of the ad
Start Date             ``startDate``       Creation date of the ad
End Date               ``endDate``         If the ad is deleted, deletion date of the ad
Bid (Micros)           ``bidMicros``       Bid of the ad for which performance metrics are calculated, in Micros
Total Spent (Micros)   ``spentMicros``     Total amount spent for this ad, in Micros
Clicks                 ``clicks``          Number of clicks that the ad received
Impressions            ``impressions``     Number of impressions that the ad received
CTR                    ``viewCTR``         Click-through rate in %
URL clicks             ``websiteClicks``   Number of URL clicks that the ad received
Emails                 ``emails``          Number of email events that the ad received
Engagement CTR         ``engagementCTR``   Engagement conversion rate in %. Calculation: ``(URL clicks + Emails) / Clicks``
Region                 ``region``          Region name, of the ad
Vendor ID              ``vendorID``        Vendor ID of the ad
====================   =================   ===============================================================


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


Report Columns V1
~~~~~~~~~~~~~~~~~

Both the excel and the csv formats contain the following columns by default:

===================   =================   ===============================================================
Name                   Field               Description
===================   =================   ===============================================================
Date (Aggregated)     ``date``             Date of the report row, grouped daily, weekly, monthly, or yearly. For daily and weekly aggregation the format is ``YYYY-MM-DD``, for monthly aggregation - ``YYYY-MM``, and for yearly - ``YYYY``. All dates are in tenant timezone.
Ad ID                 ``adID``             ID of the ad
L1 Category           ``L1Category``       Level 1 category name
L2 Category           ``L2Category``       Level 2 category name
L3 Category           ``L3Category``       Level 3 category name, if applicable
Title                 ``title``            Title of the ad
Start Date            ``startDate``        Creation date of the ad
End Date              ``endDate``          If the ad is deleted, deletion date of the ad
CPC                   ``CPC``              CPC of the ad for which performance metrics are calculated, in Local Currency
Total spent           ``spent``            Total amount spent for this ad, in Local Currency
Clicks                ``clicks``           Number of clicks that the ad received
Impressions           ``impressions``      Number of impressions that the ad received
CTR                   ``viewCTR``          Click-through rate in %
URL clicks            ``websiteClicks``    Number of URL clicks that the ad received
Emails                ``emails``           Number of email events that the ad received
Engagement CTR        ``engagementCTR``    Engagement conversion rate in %. Calculation: ``(URL clicks + Emails) / Clicks``
Region                ``region``           Region name, of the ad
Vendor ID             ``vendorID``         Vendor ID of the ad
===================   =================   ===============================================================

Examples
~~~~~~~~

.. include:: ../examples/get-metrics-ads-examples.rst


Errors
~~~~~~~~

.. include:: ../examples/get-metrics-ads-examples-errors.rst
