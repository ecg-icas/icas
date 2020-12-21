.. code-block:: javascript

    PUT /api/sellside/campaign/124512/vendorId/vendor123
    Accept: application/sellside.campaign-v2+json

    200 OK
    Content-Type: application/sellside.campaign-v2+json

    {
        "id": 124512,
        "title": "2017 garden furniture high segment",
        "dateCreated": "2016-02-03T15:35:33Z",
        "dateLastUpdated": "2016-02-03T15:35:33Z",
        "status": "ACTIVE",
        "vendorId: "vendor123",
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

    PUT /api/sellside/campaign/124512/vendorId/vendor1234
    Content-Type: application/sellside.campaign.vendor.id-v2+json

    HTTP 400 Bad Request
    Content-Type: aapplication/json; charset=utf-8
    [
        {
            "code": 2024,
            "text": "vendorId change not allowed",
            "msg": "The field 'vendorId' contains a value (vendor1234) that is different than what was previously set (vendor123)",
            "field": "vendorId",
            "arg": "vendor1234"
        }
    ]
