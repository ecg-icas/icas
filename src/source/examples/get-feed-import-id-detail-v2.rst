.. code-block:: javascript

    GET /api/sellside/feed/import/123/detail
    Accept: application/sellside.feedimportdetail-v2+json; application/json

    200 OK
    Content-Type: application/sellside.feedimportdetail-v2+json; charset=UTF-8

  {
    "id": 123,
    "url": "http://feed.com/id/5324",
    "dateCreated": "2021-08-31T16:12:53Z",
    "status": "DONE",
    "error": "",
    "totalCount": 110,
    "okCount": 106,
    "errorCount": 4,
    "warningCount": 10,
    "errors": {
        "price should be lower than originalPrice": {
            "count": 4,
            "vendorIdsSample": [
                "566",
                "abc-788",
                "990232",
                "000mcakjn"
            ]
        }
    },
    "warnings": {
        "externalId is deprecated (use only vendorId)": {
            "count": 2,
            "vendorIdsSample": [
                "vid6778787",
                "vendorid124"
            ],
        },
        "mandatory attribute 240 absent": {
            "count": 8,
            "vendorIdsSample": [
                "vendorid124",
                "vendorid224"
            ]
        }
    }
  }
