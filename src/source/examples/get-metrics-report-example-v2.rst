.. code-block:: javascript

    GET /api/sellside/metrics/report?startDate=2014-11-24&endDate=2014-11-25&status=ACTIVE,PAUSED
    Accept: application/sellside.metrics.ad-hit-v2+json

    200 OK
    Content-Type: application/sellside.metrics.ad-hit-v2+json

    {
      "createDate":"2014-12-05T14:47:04Z",
      "startDate":"2014-11-24",
      "endDate":"2014-11-25",
      "data":[
        {
          "adId":1262,
          "bidMicros":10000,
          "impressions":73,
          "clicks":43,
          "urlClicks":10,
          "emails":1,
          "engagement": 22,
          "spentMicros":430000,
          "ctr": 0.589,
          "engagementCTR": 0.511,
          "websiteCTR": 0.43,
          "startDate":"1970-01-17T09:27:18Z",
          "endDate":null,
          "title":"Test Ad",
          "categoryId":573,
          "vendorId":"vndr",
          "dailyBudgetMicros":9990000,
          "totalBudgetMicros":49000000,
          "relativePerformance": 65,
          "eSpentMicros": 4200
        }
      ]
    }
