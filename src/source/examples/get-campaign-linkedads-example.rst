.. code-block:: javascript

    GET /api/sellside/campaign/{id}/linkedAds?offset=2&limit=10&adIds=12315452,23541252,23541252
    Accept: application/sellside.campaign.linkedad-list-v1+json; charset=utf-8

    200 OK
    Content-Type: application/sellside.campaign.linkedad-list-v1+json; charset=utf-8

    [
        {
            "adId": 12315452,
            "status": "ACTIVE"
        },
        {
            "adId": 23541252,
            "status": "ACTIVE",
            "cpc": 3
        },
        {
            "adId": 23541252,
            "status": "BUDGET_REACHED",
            "cpc": 25,
            "budgets": {
                "daily": {
                    "limit": 1000,
                    "spent": 23,
                },
                "monthly": {
                    "limit": 12300,
                    "spent": 234
                },
                "total": {
                    "limit": -1,
                    "spent": 1346
                }
            }
        },
    ]
