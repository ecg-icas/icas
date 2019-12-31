.. code-block:: javascript

    POST /api/sellside/campaign/124512/budgets
    Accept: application/sellside.campaign.budgets-v2+json
    Content-Type: application/sellside.campaign.budgets-v2+json
    {
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
            "code": 2001,
            "text": "invalid argument",
            "msg": "The value of field 'budgets' was invalid"
        }
    ]






