.. index:: GET /report/detail/{id}
.. _get_report_detail_id:

GET /report/detail/{id}
=======================

:ref:`scopes` **console**

This URL returns a previously submittted report either in Excel or in CSV format depending on the
``Accept`` header. If the ``Accept`` header is ``application/vnd.ms-excel`` an Excel document is created.
If the ``Accept`` header is ``text/csv`` a `CSV <http://en.wikipedia.org/wiki/Comma-separated_values>`_ document is created.
In CSV documents values are separated by comma and double quotation marks are used around all fields.


Parameters
~~~~~~~~~~

===============  ========    ================================================================================
Name             Type        Description
===============  ========    ================================================================================
fileName         string      File name of the downloaded report. Default is **report.xls** or **report.csv**
===============  ========    ================================================================================

Report Columns
~~~~~~~~~~~~~~

Both excel and csv contain the following columns:

============     ================================================
Name             Description
============     ================================================
Date             Date of the report row
Ad id            Id of the ad
L1 Category      Level 1 category name
L2 Category      Level 2 category name
L3 Category      Level 3 category name if it exists
Title            Ad title
Start Date       The creation date of the ad
End Date         If the ad is deleted, deletion date of the ad
Total Budget     Total budget of the ad
Daily Limit      Daily budget of the ad
Total spent      Total amount spent for this ad
Cpc              Cpc of the ad
Impressions      Number of impressions that the ad received
CTR              Click through rate
Clicks           Number of clicks that the ad received
URL clicks       Number of URL clicks that the ad received
Emails           Number of email events that the ad received
External id      External id of the ad
============     ================================================

