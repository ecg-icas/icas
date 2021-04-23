.. code-block:: javascript

    GET /api/sellside/campaign/549/views/status?categoryIds=1340,1350&type=inactive&limit=5
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




