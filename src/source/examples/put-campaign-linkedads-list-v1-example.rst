.. code-block:: javascript

    PUT /api/sellside/campaign/{id}/linkedAds
    Content-Type: application/sellside.campaign-linkedads-list-v1+json; charset=utf-8

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
           "budgets":
               {
                   "daily": 1000,
                   "monthly": 12300
               }
        },
    ]
