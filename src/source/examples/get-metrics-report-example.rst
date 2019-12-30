.. code-block:: javascript

    GET /api/sellside/metricsreport?startDate=2014-11-24&endDate=2014-11-25&status=ACTIVE,PAUSED
    Accept: application/sellside.report-v3+json

    200 OK
    Content-Type: application/sellside.report-v3+json; charset=utf-8

    {
      "createDate":"2014-12-05T14:47:04Z",
      "startDate":"2014-11-24",
      "endDate":"2014-11-25",
      "data":[
        {
          "adId":1262,
          "cpc":1,
          "impressions":73,
          "clicks":43,
          "urlClicks":10,
          "emails":1,
          "engagement": 22,
          "totalSpent":43,
          "ctr": 0.589,
          "engagementCTR": 0.511,
          "websiteCTR": 0.43,
          "startDate":"1970-01-17T09:27:18Z",
          "endDate":null,
          "title":"Test Ad",
          "categoryId":573,
          "vendorId":"vndr",
          "dailyLimit":999,
          "totalBudget":4900,
          "relativePerformance": 65,
        }
      ]
    }
