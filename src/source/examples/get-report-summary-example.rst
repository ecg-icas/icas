.. code-block:: javascript

    GET /api/sellside/report/summary?startDate=2015-03-12&endDate=2015-06-21
    Accept: application/sellside.report.summary-v1+json, application/json

    200 OK
    Content-Type: application/sellside.report.summary-v1+json; charset=UTF-8

    {
      ads: 28496,
      spent: 640100,
      impressions: 162533,
      clicks: 12823,
      urlClicks: 701,
      averageCtr: 0.078894748,
      emails: 12
    }
