.. index:: GET /report/detail/{id}
.. _get_report_detail_id:

GET /report/detail/{id}
=======================

:ref:`scopes` **console**

This URL returns a previously submittted report either in ``excel`` or in ``csv`` format depending on the
``Accept`` header. If the ``Accept`` header is ``application/vnd.ms-excel`` an excel document is created.
If the ``Accept`` header is ``text/csv`` a csv document is created.


Parameters
~~~~~~~~~~

===============  ========    ================================================================================
Name             Type        Description
===============  ========    ================================================================================
fileName         string      File name of the downloaded report. Default is **report.xls** or **report.csv**.
===============  ========    ================================================================================

Report Columns
~~~~~~~~~~~~~~

Both excel and csv contain the following columns:

1. **Date:** Date of the report row.
2. **Ad id:** Id of the ad.
3. **L1 Category:** Level 1 category name.
4. **L2 Category:** Level 2 category name.
5. **L3 Category:** Level 3 category name if it exists.
6. **Title:** Ad title
7. **Start Date:** The creation date of the ad.
8. **End Date:** If the ad is deleted, deletion date of the ad.
9. **Total Budget:** Total budget of the ad.
10. **Daily Limit:** Daily budget of the ad.
11. **Total spent:** Total amount spent for this ad.
12. **Cpc:** Cpc of the ad.
13. **Impressions:** Number of impressions that the ad received.
14. **ctr:** Click through rate.
15. **Clicks:** Number of clicks that the ad received.
16. **URL Clicks:** Number of URL clicks that the ad received.
17. **Emails:** Number of email events that the ad received.
18. **External Id:** External id of the ad.

