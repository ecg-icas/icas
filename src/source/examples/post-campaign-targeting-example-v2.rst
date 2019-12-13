.. code-block:: javascript

    POST /api/sellside/campaign/124512/targeting
    Content-Type: application/sellside.campaign.targeting-v2+json
    Accept: application/sellside.campaign.targeting-v2+json
    {
        "geos": [{
            "lat": 41.234,
            "lon": 54.678,
            "radius": 40,
            "displayValue": "Amsterdam"
        }]
    }

    200 OK
    Content-Type: application/sellside.campaign.targeting-v2+json
    {
        "geos": [{
            "lat": 41.234,
            "lon": 54.678,
            "radius": 40,
            "displayValue": "Amsterdam"
        }]
    }



Setting the geo-targeting to nationwide:


.. code-block:: javascript

    POST /api/sellside/campaign/124512/targeting
    Content-Type: application/sellside.campaign.targeting-v2+json
    Accept: application/sellside.campaign.targeting-v2+json
    {
        "geos": []
    }

    200 OK
    Content-Type: application/sellside.campaign.targeting-v2+json
    {
        "geos": []
    }




Using regions targeting:

.. code-block:: javascript

    POST /api/sellside/campaign/124512/targeting
    Content-Type: application/sellside.campaign.targeting-v2+json
    Accept: application/sellside.campaign.targeting-v2+json
    {
        "regionIds": [2345,5674]
    }

    200 OK
    Content-Type: application/sellside.campaign.targeting-v2+json
    {
        "regionIds": [2345,5674]
    }







