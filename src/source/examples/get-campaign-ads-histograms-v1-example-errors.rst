.. code-block:: javascript

    GET /api/sellside/campaign/549/ads/histograms?attributes=category,region
    Accept: application/sellside.campaign.ads.histograms-v1+json
    Prefer: handling=strict

    404 Not found
    Content-Type: application/json; charset=utf-8

    [
        {
            "code": 1004,
            "text": "not found",
            "msg": "The entity was not found",
            "field": "campaignID",
            "arg": "549"
        }
    ]


.. code-block:: javascript

    GET /api/sellside/campaign/549/ads/histogram?attributes=category,blah
    Accept: application/sellside.ad-lite.list-v1+json

    400 Bad Request
    Content-Type: application/json; charset=utf-8

    [
        {
            "code": 2001,
            "text": "invalid argument",
            "msg": "The value of field 'attributes' was invalid",
            "field": "attributes",
            "arg": "blah"
        }
    ]

