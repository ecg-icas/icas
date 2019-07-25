.. code-block:: javascript

    GET /api/sellside/campaign/{id}/linkedAds?offset=2&limit=10
    Accept: application/sellside.campaign-linkedads-list-v1+json; charset=utf-8

    200 OK
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
