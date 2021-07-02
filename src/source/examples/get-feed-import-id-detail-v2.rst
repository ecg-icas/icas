.. code-block:: javascript

    GET /api/sellside/feed/import/123/detail
    Accept: application/sellside.feedimportdetail.list-v2+json; application/json

    200 OK
    Content-Type: application/sellside.feedimportdetail.list-v2+json; charset=UTF-8

  {
    "ID": 123,
    "userID": 345,
    "URL": "http://feed.com/id/1",
    "accepted": 1625219890,
    "status": 1,
    "error": "",
    "recordCount": 110,
    "acceptCount": 101,
    "rejectCount": 8,
    "noticeCount": 10,
    "tenant": "kjca",
    "errors": {
        "price should be lower than originalPrice": {
            "count": 4,
            "vendorIdsSample": [
                "566",
                "788",
                "990",
                "000"
            ]
        }
    },
    "warnings": {
        "externalId is deprecated (use only vendorId)": {
            "count": 2,
            "vendorIdsSample": [
                "vid6778787",
                "vendorid"
            ]
        },
        "mandatory attribute 240 absent": {
            "count": 8,
            "vendorIdsSample": [
                "vendorid1",
                "vendorid2"
            ]
        }
    }
  }
