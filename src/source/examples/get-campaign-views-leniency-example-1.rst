.. code-block:: javascript

    GET /api/sellside/campaign/549/views/performance?categoryIds=1,2&limit=5&bogusParam=123
    Accept: application/sellside.ad-lite.list-v1+json
    Prefer: handling=strict

    400 Bad Request
    Content-Type: application/json; charset=utf-8

    [
        {
            "code": 2001,
            "text": "unknown field name",
            "msg": "The field 'bogusParam' is unknown",
            "field": "bogusParam",
        }
    ]

.. code-block:: javascript

    GET /api/sellside/campaign/549/views/budget?reMaiNingBudgetCENTS=100&limit=5&bogusParam=123
    Accept: application/sellside.ad-lite.list-v1+json
    Prefer: handling=lenient

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
