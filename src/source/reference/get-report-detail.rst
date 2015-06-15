.. index:: GET /report/detail
.. _get_report_detail:

GET /report/detail
==================

**Required Scope:** ``console_ro``

This URL returns the list of previously submittted reports for the current user. A maximum of 3 reports
are returned. To use it set the ``Accept`` header to ``application/sellside.report.detail.list-v1+json``.


Errors
~~~~~~

There are no specific errors for this call.

Fields
~~~~~~

Each report object in the returned list contains the following fields.

==============  ======  =====================================================
Field           Type    Description
==============  ======  =====================================================
id              string  Unique id of the report
dateCreated     date    Creation date of the report
startDate       date    Start date of the report
endDate         date    End date of the report
includeDeleted  bool    Deleted ads are included/excluded
count           int     Number of rows in the report
==============  ======  =====================================================

Example
~~~~~~~

.. include:: ../examples/get-report-detail-example.rst
