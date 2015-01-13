.. code-block:: javascript

    GET /api/sellside/report?startDate=2014-11-24&endDate=2014-11-25
    Accept: application/sellside.report-v2+json

    200 OK
    Content-Type: application/sellside.report-v2+json

    {
      "createDate":"2014-12-05T14:47:04Z",
      "startDate":"2014-11-23T23:00:00Z",
      "endDate":"2014-11-24T23:00:00Z",
      "data":[
        {
          "adId":1262,
          "categoryId":573,
          "title":"Test Ad",
          "startDate":"1970-01-17T09:27:18Z",
          "endDate":null,
          "totalBudget":4900,
          "dailyLimit":999,
          "totalSpent":43,
          "cpc":1,
          "impressions":13,
          "clicks":43,
          "urlClicks":73,
          "emails":0,
          "externalId":"ad123ecec"
        }
      ]
    }