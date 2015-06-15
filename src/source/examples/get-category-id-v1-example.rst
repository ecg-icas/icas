.. code-block:: javascript

    GET /category/?levels=1
    Accept: application/sellside.category-v1+json, application/json

    200 OK
    Content-Type: application/sellside.category-v1+json; charset=utf-8

    {
        "children": [
            {
                "id": 1,
                "links": {
                    "attributes": "/category/1/attributes",
                    "self": "/category/1"
                },
                "currency": "EUR",
                "maxCpc": 250,
                "maxTotalBudget": 2000000,
                "minCpc": 1,
                "minTotalBudget": 5000,
                "minDailyBudget": 2000,
                "canPlaceAds": true,
                "maxNumberOfActiveAds": 7000,
                "name": "Antiek en Kunst",
                "suggestedCpcForPageOne" : 55
            },
            {
                "id": 31,
                "links": {
                    "attributes": "/category/31/attributes",
                    "self": "/category/31"
                },
                "currency": "EUR",
                "maxCpc": 250,
                "maxTotalBudget": 2000000,
                "minCpc": 1,
                "minTotalBudget": 5000,
                "minDailyBudget": 2000,
                "canPlaceAds": true,
                "maxNumberOfActiveAds": 7000,
                "name": "Audio, Tv en Foto",
                "suggestedCpcForPageOne" : 72
            },
            ...
        ],
        "id": 22,
        "links": {
            "attributes": "/category/22/attributes",
            "self": "/category/22"
        },
        "currency": "EUR",
        "maxCpc": 0,
        "maxTotalBudget": 0,
        "minCpc": 0,
        "minTotalBudget": 0,
        "minDailyBudget": 0,
        "canPlaceAds": false,
        "maxNumberOfActiveAds": 0,
        "name": "root"
    }

