.. index:: GET /report/summary

.. _get_report_summary:

GET /report/summary
===================

:ref:`get_report_summary_v2` | :ref:`get_report_summary_v1`

.. _get_report_summary_v2:

GET /report/summary V2
----------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/sellside.report.summary-v2+json, application/json``


.. warning::

	This call is scheduled to be deprecated. Please
	use the faster and more flexible replacement generic endpoint :ref:`post_metrics_data` instead. Check the first example in the :ref:`examples_post_metrics_data` section.


This URL returns the summarized performance data for all ads (including deleted) from the user in the provided period.

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
spent           int     Spent amount for all ads in the period
impressions     int     Number of impressions for all ads in the period
clicks          int     Number of clicks for all ads in the period
engagement      int     Number of leads generated (clickouts, emails, ...)
averageCtr      double  Average ctr over all ads in the period, in percentages
==============  ======  =====================================================

Example
~~~~~~~

.. include:: ../examples/get-report-summary-example-v2.rst


.. _get_report_summary_v1:

GET /report/summary V1
----------------------

*Deprecated*. Please use :ref:`get_report_summary_v2`.


.. list-table::
 :widths: 20 80

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/sellside.report.summary-v1+json, application/json``

This URL returns the summarized performance data for all ads (including deleted) from the user in the provided period.

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
averageCtr      double  Average ctr over all ads in the period, in percentages
emails          int     Number of emails for all ads in the period
==============  ======  =====================================================

Example
~~~~~~~

.. include:: ../examples/get-report-summary-example.rst
