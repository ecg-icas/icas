.. index:: POST /report/detail
.. _post_report_detail:

POST /report/detail
===================

:ref:`scopes` **console**

This URL submits a new report request for the current user.
Report creation is a long running process and contains the following steps:

1. Submit a report request by posting to this URL. This will start report creation and return the unique report id.
2. Get the list of submitted reports using :doc:`get-report-detail` and check whether the submitted report is ready
   by checking the id obtained at step 1.
3. When the report is ready download the report using :doc:`get-report-detail-id`.

Fields
~~~~~~

Field of the report request is as follows:

==============  ======  ==================  =====================================================
Field           Type    Mandatory           Description
==============  ======  ==================  =====================================================
startDate       string  yes                 Start date of the report in 'yyyy-MM-dd' format
endDate         string  yes                 End date of the report in 'yyyy-MM-dd' format
includeDeleted  bool    no - Default false  Whether the deleted ads are included in report or not
==============  ======  ==================  =====================================================

Errors
~~~~~~

Both startDate and endDate fields in the request must be in 'yyyy-MM-dd' format. Both fields must point to dates in the past.

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
startDate               2000    missing argument            The field 'startDate' was missing
startDate               2001    invalid argument            The value of field 'startDate' was invalid
startDate               2002    out of range                The value of the field 'startDate' was out of range
startDate               2004    too short                   The minimum length of field 'startDate' is 1 characters
endDate                 2000    missing argument            The field 'endDate' was missing
endDate                 2001    invalid argument            The value of field 'endDate' was invalid
endDate                 2002    out of range                The value of the field 'endDate' was out of range
endDate                 2004    too short                   The minimum length of field 'endDate' is 1 characters
====================    ====    =======================     ==============================================================================

Example Request
~~~~~~~~~~~~~~~

.. include:: ../examples/post-report-detail-req-example.rst

Example Response
~~~~~~~~~~~~~~~~

.. include:: ../examples/post-report-detail-res-example.rst
