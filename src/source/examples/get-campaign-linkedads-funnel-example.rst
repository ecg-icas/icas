.. code-block:: javascript

    GET /api/sellside/campaign/718089/linkedAds/1267273610/funnel?cpc=3
    Accept: application/sellside.campaign.linkedad.funnel-v1+json

    200 OK
    Content-Type: application/sellside.campaign.linkedad.funnel-v1+json

    {
        "cpc": {
            "low": 1,
            "medium": 2,
            "high": 6,
            "firstPage": 5
        },
        "performance": {
            "impressions": 419,
            "clicks": 44,
            "websiteClicks": 11,
            "viewCTR": 0.10576595018764927,
            "websiteCTR": 0.24193548387096775
        },
        "position": {
            "pageNumber": 3
        }
    }

