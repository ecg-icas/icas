.. code-block:: javascript

    {
       "adId": <number>,
       "status": <string>,
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
``status``             The current status of this linkedAd. One of ``ACTIVE`` or ``BUDGET_REACHED``
``cpc``               Instead of using the campaign's CPC, use this override (cents)
``budgets``             An object containing the budget limits for the linkedAd. Does not void campaign budgets. The limits unit is cents. The default values are set to **-1 (Unlimited)**.
===================  =========================================================================================

