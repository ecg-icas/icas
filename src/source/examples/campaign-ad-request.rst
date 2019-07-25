.. code-block:: javascript

    {
       "adId": <number>,
       "cpc": <number>,
       "budgets":
           {
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
``adId``              A description of your campaign. Only visible on your dashboard, it will never be shown to buyers.
``cpc``               Instead of using the campaign's CPC, use this override (cents)
``budgets``             An object containing the budget limits for the linkedAd. Does not void campaign budgets. The limits unit is cents. The default values are set to **-1 (Unlimited)**.
===================  =========================================================================================

