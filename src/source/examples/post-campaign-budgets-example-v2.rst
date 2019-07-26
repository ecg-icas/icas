.. code-block:: javascript

    POST /api/sellside/campaign/124512/budgets
    Accept: application/sellside.campaign-budgets-v2+json
    Content-Type: application/sellside.campaign-budgets-v2+json
    "budgets": {
        "daily": {
            "limit": 1000
        },
        "monthly": {
            "limit": 12300
        }
    }    

    200 OK
    Content-Type: application/sellside.campaign-budgets-v2+json

    "budgets": {
        "daily": {
            "limit": 1000,
            "spent": 23,
        },
        "monthly": {
            "limit": 12300,
            "spent": 234
        },
        "total": {
            "limit": -1,
            "spent": 1346
        }
    }