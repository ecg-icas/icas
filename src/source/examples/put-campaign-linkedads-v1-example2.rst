.. code-block:: javascript

    PUT /api/sellside/campaign/123/linkedAds
    Accept: application/sellside.campaign.linkedad-v1+json; charset=utf-8
    Content-Type: application/sellside.campaign.linkedad-v1+json; charset=utf-8

    {
       "adId": 12315452,
       "autoBid": true
    }

    400 Bad Request
    Content-Type: application/json
    [
        {
            "code": 2040,
            "text": "campaign deleted",
            "msg": "The campaign is DELETED, setting linkedAds not allowed",
        }
    ]
