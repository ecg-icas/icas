.. index:: POST /report/detail
.. _post_report_detail:

POST /report/detail
===================

:ref:`scopes` **console**

This URL requests a new report for the current user.
Creating the report may take a long time which depends on the number of ads and the requested date range. Therefore you

1. Request a new report with `POST /report/detail` which returns a unique id
2. Poll `GET /report/detail` until the id is in the result
3. Fetch the report with `GET /report/detail/{id}`

Fields
~~~~~~

Field of the report request is as follows:

==============  ======  ==================  =====================================================
Field           Type    Mandatory           Description
==============  ======  ==================  =====================================================
startDate       string  yes                 Start date of the report in yyyy-MM-dd format
endDate         string  yes                 End date of the report in yyyy-MM-dd format
includeDeleted  bool    no                  Deleted ads are included/excluded. Default `false`
==============  ======  ==================  =====================================================

Errors
~~~~~~

Both `startDate` and `endDate` fields in the request must be in yyyy-MM-dd format. Both fields must point to dates in the past.

====================    ====    =======================     ==============================================================================
Field                   Code    Error message               Description
====================    ====    =======================     ==============================================================================
startDate               2000    missing argument            The field `startDate` was missing
startDate               2001    invalid argument            The value of field `startDate` was invalid
startDate               2002    out of range                The value of the field `startDate` was out of range
startDate               2004    too short                   The minimum length of field `startDate` is 1 characters
endDate                 2000    missing argument            The field `endDate` was missing
endDate                 2001    invalid argument            The value of field `endDate` was invalid
endDate                 2002    out of range                The value of the field `endDate` was out of range
endDate                 2004    too short                   The minimum length of field `endDate` is 1 characters
====================    ====    =======================     ==============================================================================

Example Request
~~~~~~~~~~~~~~~

.. include:: ../examples/post-report-detail-req-example.rst

Example Response
~~~~~~~~~~~~~~~~

.. include:: ../examples/post-report-detail-res-example.rst