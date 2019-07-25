.. code-block:: javascript

    GET /api/sellside/campaign/byVendor/my-christmas-campaign-3A
    Accept: application/sellside.campaign-v2+json

    200 OK
    Content-Type: application/sellside.campaign-v2+json

    {
        "id": 1234,
        "title": "My christmas campaign",
        "dateCreated": "2016-02-03T15:35:33Z",
        "dateLastUpdated": "2016-02-03T15:35:33Z",
        "status": "ACTIVE",
        "vendorId: "my-christmas-campaign-3A"
    }
