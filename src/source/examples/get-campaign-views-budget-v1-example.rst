Get the top 5 ads in campaign 549 which are almost out of budget, with 100 or less remaining cents (they will be sorted by the least amount of remaining total budget):

.. code-block:: javascript

    GET /api/sellside/campaign/549/views/budget?remainingBudgetCents=100&limit=5
    Accept: application/sellside.ad-lite.list-v1+json

    200 OK
    Content-Type: application/sellside.ad-lite.list-v1+json

    {
        "data": [
            {
                "adId": 1201904691
            },
            {
                "adId": 1201904690
            },
            {
                "adId": 1201904689
            },
            {
                "adId": 1201904688
            },
            {
                "adId": 1201904687
            }
        ],
        "total": 6,
        "nextPageToken": "eyJpZCI6MTIwMTkwNDY4Niwic3RyaW5nX3ZhbHVlIjpudWxsLCJpbnQ2NF92YWx1ZSI6bnVsbH0"
    }

Get the top 5 ads in campaign 549 which are out of total ad-level budget:

.. code-block:: javascript

    GET /api/sellside/campaign/549/views/budget?outOfBudget=true&limit=5
    Accept: application/sellside.ad-lite.list-v1+json

    200 OK
    Content-Type: application/sellside.ad-lite.list-v1+json

    {
        "data": [
            {
                "adId": 1202053784
            }
        ],
        "total": 1,
        "nextPageToken": null
    }

**Beware** that in the above example, there could still be some remaining cents, but due to the cost per click set on this ad, it is impossible to spend that remaining amount, so the ad is declared out of budget.
