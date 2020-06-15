.. code-block:: javascript

    PUT /api/sellside/campaign/124512/budgets
    Accept: application/sellside.campaign.budgets-v2+json
    Content-Type: application/sellside.campaign.budgets-v2+json
    {}

    200 OK
    Content-Type: application/sellside.campaign.budgets-v2+json
    {
        "daily": {
            "limit": -1,
            "spent": 23
        },
        "monthly": {
            "limit": -1,
            "spent": 234
        },
        "total": {
            "limit": -1,
            "spent": 1346
        }
    }








