.. code-block:: javascript

    PUT /api/sellside/campaign/123/linkedAds
    Accept: application/sellside.campaign.linkedad-v1+json; charset=utf-8
    Content-Type: application/sellside.campaign.linkedad-v1+json; charset=utf-8

    {
       "adId": 12315452,
       "autoBid": true
    }

    HTTP 200 OK
    Content-Type: application/sellside.campaign.linkedad-v1+json; charset=utf-8

    {
       "adId": 12315452,
       "status": "ACTIVE"
       "autoBid": true
    }
