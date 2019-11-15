.. code-block:: javascript

    {
       "adId": <number>,
       "status": <string>,
       "cpc": <number>,
       "budgets": {
            "daily": {
                "limit": <number>,
                    "spent": <number>
                },
            "monthly": {
                "limit": <number>,
                "spent": <number>
            },
            "total": {
                "limit": <number>,
                "spent": <number>
            }
        }
    }


===================  =========================================================================================
Field                 Description
===================  =========================================================================================
``adId``              The ID of the ad that this linkedAd refers to
``status``            The current status of this linkedAd. One of ``ACTIVE`` or ``BUDGET_REACHED``. This is read-only field
``cpc``               Instead of using the campaign's CPC, use this override (cents)
``budgets``           An object containing the budget current limits and spent for the linkedAd. Does not void campaign budgets. The unit for ``limit`` and ``spent`` is cents. The default ``limit`` values are set to **-1 (Unlimited)**
===================  =========================================================================================

