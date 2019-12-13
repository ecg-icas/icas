.. code-block:: javascript

    POST /api/sellside/campaign/124512/budgets
    Accept: application/sellside.campaign.budgets-v2+json
    Content-Type: application/sellside.campaign.budgets-v2+json
    "budgets": {
        "daily": {
            "limit": 1000
        },
        "monthly": {
            "limit": 12300
        }
    } 

    400 Bad Request
    Content-Type: application/json
    [
        {
            "code": 2040,
            "text": "campaign deleted",
            "msg": "The campaign is DELETED, setting budgets not allowed",
        }
    ]



