.. code-block:: javascript

    GET /campaigns?limit=2
    Accept: application/sellside.campaign.list-v5+json, application/json

    200 OK HTTP/1.1
    Content-Type: application/sellside.campaign.list-v5+json; charset=UTF-8

    {
        [
            {
                "id": 123,
                "dateCreated": "2022-12-25T10:04:23Z",
                "dateLastUpdated": "2022-12-28T22:40:15Z",
                "status": "ACTIVE",
                "vendorId": "123-abc-vjlkna-124",
                "title": "christmas stuff",
                "isDefault": true,
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
            },
            {
                "id": 456,
                "dateCreated": "2023-08-23T15:33:531Z",
                "dateLastUpdated": "2023-08-28T17:12:32Z",
                "status": "ACTIVE",
                "vendorId": "456-asf-fdshgsd-12",
                "title": "autumn sale",
                "isDefault": false,
                "budgets": {
                    "daily": {
                        "limitMicros": "10000000",
                        "spentMicros": "210000",
                    },
                    "total": {
                        "limitMicros": "100000000",
                        "spentMicros": "6210000",
                    }
                }
            }
        ],
        "total": 10,
        "nextPageToken": "ldsknv-12414-2t-svsdvjksndfhgkjls-1312352asfasdg"
    }