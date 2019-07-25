.. code-block:: javascript

    PUT /api/sellside/campaign/{id}/linkedAds
    Accept: application/sellside.campaign-linkedads-list-v1+json; charset=utf-8
    Content-Type: application/sellside.campaign-linkedads-list-v1+json; charset=utf-8

    [
        {
           "adId": 12315452
        },
        {
           "adId": 23541252,
           "cpc": 3
        },
        {
           "adId": 23541252,
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

    HTTP 200 OK
    Content-Type: application/sellside.campaign-linkedads-list-v1+json; charset=utf-8

    [
        {
           "adId": 12315452,
           "status": ACTIVE
        },
        {
           "adId": 23541252,
           "status": ACTIVE,
           "cpc": 3
        },
        {
           "adId": 23541252,
           "status": ACTIVE,
           "cpc": 25,
           "budgets":
               {
                   "daily": {
                        "limit": 1000,
                        "spent": 10
                    },
                   "monthly": {
                        "limit": 12300,
                        "spent": 100
                    },
                    "total": {
                        "limit": -1,
                        "spent": 123
                    }
               }
        },
    ]
