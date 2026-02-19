.. code-block:: javascript

    GET /api/sellside/categories/statistics?categoryIds=2412,525,4216&date=2017-11-09
    Accept: application/sellside.category.statistics-v1+json; application/json

    200 OK
    Content-Type: application/sellside.category.statistics-v1+json; charset=utf-8

    [
        {
            "categoryId": 525,
            "numAds": 3,
            "impressions": 60,
            "clicks": 42,
            "urlClicks": 21,
            "emails": 6,
            "spent": 126
        },
        {
            "categoryId": 2412,
            "numAds": 21,
            "impressions": 630,
            "clicks": 72,
            "urlClicks": 21,
            "emails": 0,
            "spent": 1262
        }
    ]