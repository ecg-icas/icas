.. code-block:: javascript

    PUT /api/sellside/campaign/{id}/linkedAds
    Accept: application/sellside.campaign-linkedads-v1+json; charset=utf-8
    Content-Type: application/sellside.campaign-linkedads-v1+json; charset=utf-8

    {
       "adId": 12315452,
       "cpc": 3
    }

    HTTP 200 OK
    Content-Type: application/sellside.campaign-linkedads-v1+json; charset=utf-8

    {
       "adId": 12315452,
       "status": "ACTIVE"
       "cpc": 3
    }
