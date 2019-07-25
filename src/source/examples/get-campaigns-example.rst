.. code-block:: javascript

    GET /api/sellside/campaigns?status=ACTIVE,PAUSED&offset=2&limit=10
    Accept: application/sellside.campaign.list-v2+json

    200 OK
    Content-Type: application/sellside.campaign.list-v2+json; charset=utf-8

    {
        "campaigns": {
            [
                {
                    "id": 1234,
                    "title": "Test campaign",
                    "dateCreated": "2016-02-03T15:35:33Z",
                    "dateLastUpdated": "2016-02-03T15:35:33Z",
                    "status": "ACTIVE",
                    "cpc": 10,
                    "budgets": {
                        "daily": {
                            "limit": 120,
                            "spent": 20
                        },
                        "monthly": {
                            "limit": 1000,
                            "spent": 30
                        },
                        "total": {
                            "limit": -1,
                            "spent":30
                        }
                    },
                    "targeting": {
                        "geos": [{
                            "lat": 1.234,
                            "lon": 5.678,
                            "radius": 10,
                            "type": "zip",
                            "value": "1000AB",
                            "displayValue": "Amsterdam"
                            }],
                        "regionIds": [9007, 9008]
                    }
                    "links": {
                        "listings": "api/sellside/campaign/1234/linkedAds"
                    }
                }
            ]
        },
    "total": 30
    }
