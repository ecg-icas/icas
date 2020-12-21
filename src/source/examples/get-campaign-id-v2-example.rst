.. code-block:: javascript

    GET /api/sellside/campaign/124512
    Accept: application/sellside.campaign-v2+json

    200 OK
    Content-Type: application/sellside.campaign-v2+json

    {
        "id": 124512,
        "title": "2017 garden furniture high segment",
        "dateCreated": "2016-02-03T15:35:33Z",
        "dateLastUpdated": "2016-02-03T15:35:33Z",
        "status": "ACTIVE",
        "vendorId: "201907-garden-furniture-II",
        "budgets": {
            "daily": {
                "limit": -1,
                "spent": 10
            },
            "monthly": {
                "limit": -1,
                "spent": 100
            },
            "total": {
                "limit": 2000,
                "spent": 1000
            }
        },
        "targeting": {
            "geos": [{
                "lat": 41.234,
                "lon": 54.678,
                "radius": 40,
                "displayValue": "Amsterdam"
            }],
            "regionIds": []
        }
    }
