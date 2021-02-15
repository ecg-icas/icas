.. code-block:: javascript

    {
        "adId": <number>,
        "status": <string>,
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
        "autoBid": <bool>
    }


===================  =========================================================================================
Field                 Description
===================  =========================================================================================
``adId``              The ID of the ad that this linkedAd refers to. This field is mandatory.
``status``            The status of the linkedAd.  One of ``ACTIVE``, ``PAUSED``. If not provided, it will default to ``ACTIVE``.
``cpc``               The CPC (in cents) to use for this ad in the context of the given campaign. This field is mandatory if ``autoBid`` is ``false``.
``budgets``           An object containing the budget limits for the linkedAd. Does not void campaign budgets. The ``limits`` unit is cents. If not supplied, the default values are set to **-1 (Unlimited)**.
``autoBid``           Whether the automatic bidding agent should act on the cost (per click, for now) and budgets on this ad within the given campaign. If the value is ``true``, the payload should **not** contain the ``cpc`` and ``budgets`` fields, they will be auto-managed instead. Not every user is enabled for this functionality; if interested, please get in touch with us on Discord. Default value is ``false``.
===================  =========================================================================================

