.. code-block:: javascript

    POST /api/sellside/campaign
    Accept: application/sellside.campaign-v2+json
    Content-Type: application/sellside.campaign-v2+json
    {}

    201 Created
    Content-Type: application/sellside.campaign-v2+json
     {
        "id": 1234,
        "dateCreated": "2016-02-03T15:35:33Z",
        "dateLastUpdated": "2016-02-03T15:35:33Z",
        "status": "PAUSED",
        "budgets": {
            "daily": {
                "limit": -1,
                "spent": 0
            },
            "monthly": {
                "limit": -1,
                "spent": 0
            },
            "total": {
                "limit": -1,
                "spent": 0
            }
        }
    }
