.. code-block:: javascript

    PUT /campaign/123/budgets
    Accept: application/sellside.campaign-budgets-v5+json, application/json

    {
        "budgets": {
            "daily": {
                "limitMicros": "10000000",
            },
            "total": {
                "limitMicros": "UNLIMITED",
            }
        }
    }


    200 OK HTTP/1.1
    Content-Type: application/sellside.campaign-budgets-v5+json; charset=UTF-8

    {
        "budgets": {
            "daily": {
                "limitMicros": "10000000",
                "spentMicros": "9520000",
            },
            "total": {
                "limitMicros": "UNLIMITED",
                "spentMicros": "124520000",
            }
        }
    }