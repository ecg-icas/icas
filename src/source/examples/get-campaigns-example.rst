.. code-block:: javascript

    GET /api/sellside/campaigns?status=ACTIVE,PAUSED&offset=2&limit=10
    Accept: application/sellside.campaign.list-v2+json

    200 OK
    Content-Type: application/sellside.campaign.list-v2+json

    {
        "campaigns": {
            [
                {
                    "id": 1234,
                    "title": "Test campaign",
                    "dateCreated": "2016-02-03T15:35:33Z",
                    "dateLastUpdated": "2016-02-03T15:35:33Z",
                    "status": "ACTIVE",
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
                            "displayValue": "Amsterdam"
                        }]
                    }
                }
            ]
        },
    "total": 30
    }

    GET /api/sellside/campaigns?status=DELETED&offset=2&limit=10
    Accept: application/sellside.campaign.list-v2+json

    200 OK
    Content-Type: application/sellside.campaign.list-v2+json

    {
        "campaigns": {
            [
                {
                    "id": 1234,
                    "title": "Test campaign",
                    "dateCreated": "2016-02-03T15:35:33Z",
                    "dateLastUpdated": "2018-02-03T15:35:33Z",
                    "status": "DELETED",
                    "targeting": {
                        "geos": [{
                            "lat": 1.234,
                            "lon": 5.678,
                            "radius": 10,
                            "displayValue": "Amsterdam"
                        }]
                    }
                }
            ]
        },
    "total": 2
    }
