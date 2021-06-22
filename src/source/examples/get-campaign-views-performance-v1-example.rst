.. code-block:: javascript

    GET /api/sellside/campaign/549/views/performance?limit=10&type=highSpend&startDate=2020-01-31&endDate=2020-02-20
    Accept: application/sellside.ad-lite.list-v1+json

    200 OK
    Content-Type: application/sellside.ad-lite.list-v1+json

    {
        "data": [
            {
                "adId": 1201904695
            },
            {
                "adId": 1201904696
            }
        ],
        "total": 2
    }

