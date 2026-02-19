.. code-block:: javascript

    POST /campaign
    Accept: application/sellside.campaign-v5+json, application/json
    Content-Type: application/sellside.campaign-v5+json; charset=UTF-8

    {
        "status": "ACTIVE",
        "budgets": {
            "daily": {
                "limitMicros": "10000000",
            },
            "total": {
                "limitMicros": "UNLIMITED",
            }
        }
    }

    200 OK HTTP/1.1
    Content-Type: application/sellside.campaign-v5+json; charset=UTF-8

    {
        "id": 123,
        "dateCreated": "2022-12-25T10:04:23Z",
        "dateLastUpdated": "2022-12-28T22:40:15Z",
        "status": "ACTIVE",
        "budgets": {
            "daily": {
                "limitMicros": "10000000",
                "spentMicros": "0",
            },
            "total": {
                "limitMicros": "UNLIMITED",
                "spentMicros": "0",
            }
        }
    }
