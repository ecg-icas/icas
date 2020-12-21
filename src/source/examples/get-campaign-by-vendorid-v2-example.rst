.. code-block:: javascript

    GET /api/sellside/campaign/byVendor/my-christmas-campaign-3A
    Accept: application/sellside.campaign-v2+json

    200 OK
    Content-Type: application/sellside.campaign-v2+json

    {
        "id": 1234,
        "title": "My christmas campaign",
        "dateCreated": "2016-02-03T15:35:33Z",
        "dateLastUpdated": "2016-02-03T15:35:33Z",
        "status": "ACTIVE",
        "vendorId: "my-christmas-campaign-3A",
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
