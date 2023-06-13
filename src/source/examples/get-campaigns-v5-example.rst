.. code-block:: javascript

    GET /campaigns
    Accept: application/sellside.campaign.list-v5+json, application/json

    200 OK HTTP/1.1
    Content-Type: application/sellside.campaign.list-v5+json; charset=UTF-8

    [
        {
            "id": 123,
            "dateCreated": "2022-12-25T10:04:23Z",
            "dateLastUpdated": "2022-12-28T22:40:15Z",
            "status": "ACTIVE",
            "budgets": {
                "daily": {
                    "limitMicros": "10000000",
                    "spentMicros": "9520000",
                },
                "total": {
                    "limitMicros": "UNLIMITED",
                    "spentMicros": "124520000",
                }
            }
        }
    ]
