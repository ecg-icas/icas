.. index:: GET /report/detail
.. _get_report_detail:

GET /report/detail
==================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/sellside.report.detail.list-v1+json, application/json``


.. warning::

	This call is scheduled to be deprecated. Please
	use the faster and synchronous replacement endpoint :ref:`get_metrics_ads` instead.
	Keep in mind that the new endpoint only returns data for **ads which have had performance-related activity in the requested period**.


This URL returns the list of previously submitted reports for the current
user. A maximum of 3 reports are returned.


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
"""""""

.. include:: ../examples/get-report-detail-example.rst
