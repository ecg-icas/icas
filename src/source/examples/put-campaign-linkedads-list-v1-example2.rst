.. code-block:: javascript

    PUT /api/sellside/campaign/123/linkedAds
    Accept: application/sellside.campaign.linkedad-list-v1+json; charset=utf-8
    Content-Type: application/sellside.campaign.linkedad-list-v1+json; charset=utf-8

    [
        {
           "adId": 12315452,
           "autoBid": true
        },
        {
           "adId": 23541253,
           "cpc": 3
        },
        {
           "adId": 23541254,
           "cpc": 25,
           "budgets":
           {
               "daily": {
                    "limit": 1000
                },
               "monthly": {
                    "limit": 12300
                },
                "total": {
                    "limit": -1
                }
           }
        },
    ]

    400 Bad Request
    Content-Type: application/json
    [
        {
            "code": 2040,
            "text": "campaign deleted",
            "msg": "The campaign is DELETED, setting linkedAds not allowed",
        }
    ]
