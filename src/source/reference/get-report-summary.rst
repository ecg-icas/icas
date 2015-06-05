.. index:: GET /report/summary
.. _get_report_summary:

GET /report/summary
===================

:ref:`scopes` **report**

This URL returns the summarized performance data for all ads (including deleted) from the user in the provided period.
To use it set the ``Accept`` header to ``application/sellside.report.summary-v1+json``.

Parameters
~~~~~~~~~~

====================    ======    ============================================================================================
Name                    Type      Description
====================    ======    ============================================================================================
startDate               String    Start date of the period for the report summary. Must be a valid date in format 'yyyy-MM-dd'
endDate                 String    End date of the period for the report summary. Must be a valid date in format 'yyyy-MM-dd'
====================    ======    ============================================================================================


Errors
~~~~~~

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
startDate               2001    invalid argument            must be a valid date in format 'yyyy-MM-dd'
endDate                 2001    invalid argument            must be a valid date in format 'yyyy-MM-dd'
startDate/endDate       2002    out of range                endDate should be after startDate
====================    ====    =======================     ==============================================================================

Fields
~~~~~~

The returned object is as follows.

==============  ======  =====================================================
Field           Type    Description
==============  ======  =====================================================
ads             int     Number of ads with activity in the period
spent           int     Spent amount for all ads in the period
impressions     int     Number of impressions for all ads in the period
clicks          int     Number of clicks for all ads in the period
urlClicks       int     Number of urlClicks for all ads in the period
averageCtr      double  Average ctr over all ads in the period
emails          int     Number of emails for all ads in the period
==============  ======  =====================================================

Example
~~~~~~~

.. include:: ../examples/get-report-summary-example.rst
