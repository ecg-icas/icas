.. code-block:: javascript

    GET /api/sellside/campaign/549/ads/histograms?attributes=category,region
    Accept: application/sellside.campaign.ads.histograms-v1+json
    Prefer: handling=strict

    200 OK
    Content-Type: application/sellside.campaign.ads.histograms-v1+json

    {
        "categories": {
            "counts": {
                "12": 1,
                "133": 3,
                "140": 2,
                "14970007": 1,
                "15": 2,
                "15093002": 19,
                "317": 28639,
                "318": 4144,
                "320": 8996,
                "321": 214,
                "655": 7186,
                "719": 4,
                "769": 1,
                "770": 1,
                "87": 105997
            }
        },
        "regions": {
            "counts": {
                "0": 42004,
                "1700118": 1,
                "1700234": 7,
                "1700261": 1,
                "1700274": 1,
                "9000": 1,
                "9003": 1,
                "9004": 9,
                "9007": 1
            }
        }
    }

