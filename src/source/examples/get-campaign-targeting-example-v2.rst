.. code-block:: javascript

    GET /api/sellside/campaign/124512/targeting
    Accept: application/sellside.campaign-targeting-v2+json

    200 OK
    Content-Type: application/sellside.campaign-targeting-v2+json

    {
        "geos": [{
            "lat": 41.234,
            "lon": 54.678,
            "radius": 40,
            "displayValue": "Amsterdam"
        }]
    }


