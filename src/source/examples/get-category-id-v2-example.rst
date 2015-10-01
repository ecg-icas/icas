.. code-block:: javascript

    GET /api/sellside/category/2?levels=1
    Accept: application/sellside.category-v2+json; application/json

    200 OK
    Content-Length: 789
    Content-Type: application/sellside.category-v2+json; charset=UTF-8

    {
        "links": {
            "parent": "/api/sellside/category/1",
            "self": "/api/sellside/category/2"
        },
        "id": 2,
        "parentId": 1,
        "level": 2,
        "path": "1_2",
        "locales": [
            "nl_NL"
        ],
        "label": {
            "nl_NL": "Antiek | Bestek"
        },
        "breadcrumbs": {
            "nl_NL": [
                "Antiek en Kunst",
                "Antiek | Bestek"
            ]
        },
        "status": "ACTIVE",
        "config": {
            "cpc": "[1,250]",
            "totalBudget": "[5000,200000000]",
            "minDailyBudget": 1000,
            "activeAds": "[1,7000]",
            "titleLength": "[1,60]",
            "descriptionLength": "[1,20000]",
            "images": "[0,8]",
            "urlMandatory": false,
            "shippingOption": "DISABLED",
            "paypalEnabled": true,
            "paypalBpEnabled": true,
            "currency": "EUR",
            "priceTypes": [
                "BIDDING",
                "BIDDING_FROM",
                "FIXED_PRICE",
                "FREE",
                "NEGOTIABLE",
                "SEE_DESCRIPTION",
                "SWAP",
                "CREDIBLE_BID",
                "ON_DEMAND",
                "RESERVED"
            ],
            "priceUnits": {},
            "verticals": [],
            "tags": {},
            "region": "DISABLED",
            "relatedPaths": [
                "1_2614",
                "1_15",
                "504_1941"
            ]
        }
    }