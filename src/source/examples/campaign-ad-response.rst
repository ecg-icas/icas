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
        },
        "autoBid": <bool>
    }


===================  =========================================================================================
Field                 Description
===================  =========================================================================================
``adId``              The ID of the ad that this linkedAd refers to
``status``            The current status of this linkedAd. One of ``ACTIVE`` or ``BUDGET_REACHED``. This is read-only field
``cpc``               The CPC (in cents) to use for this ad in the context of the given campaign. If ``autoBid`` is ``true``, this field is omitted.
``budgets``           An object containing the budget current limits and spent for the linkedAd. Does not void campaign budgets. The unit for ``limit`` and ``spent`` is cents. If ``autoBid`` is ``true``, this field is omitted.
``autobid``           Whether the automatic bidding agent should act on the cost (per click, for now) and budgets on this ad within the given campaign. If the value is ``true``, the response payload will **not** contain the ``cpc`` and ``budgets`` fields. If interested in this functionality, get in touch with us on Discord
===================  =========================================================================================

