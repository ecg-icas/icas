.. code-block:: javascript

    {
        "adId": <number>,
        "cpc": <number>,
        "budgets": {
            "daily": {
                "limit": <number>
            },
            "monthly": {
                "limit": <number>
            },
            "total": {
                "limit": <number>
            }
        }
    }


===================  =========================================================================================
Field                 Description
===================  =========================================================================================
``adId``              The ID of the ad that this linkedAd refers to.
``cpc``               Instead of using the campaign's CPC, use this override (cents)
``budgets``             An object containing the budget limits for the linkedAd. Does not void campaign budgets. The ``limits`` unit is cents. The default values are set to **-1 (Unlimited)**.
===================  =========================================================================================

