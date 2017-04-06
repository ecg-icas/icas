.. code-block:: javascript

    GET /api/sellside/report/summary?startDate=2015-03-12&endDate=2015-06-21
    Accept: application/sellside.report.summary-v2+json, application/json

    200 OK
    Content-Type: application/sellside.report.summary-v2+json; charset=utf-8

    {
      spent: 640100,
      impressions: 162533,
      clicks: 12823,
      engagement: 713,
      averageCtr: 0.078894748
    }
