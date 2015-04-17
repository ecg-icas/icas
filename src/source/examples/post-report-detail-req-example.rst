.. code-block:: javascript

    POST /api/sellside/report/detail
    Accept: application/sellside.detail.report.response-v1+json, application/json
    Content-Type: application/sellside.detail.report.request-v1+json

    {
        "startDate": "2015-04-04",
        "endDate": "2015-04-17",
        "includeDeleted": true
    }
