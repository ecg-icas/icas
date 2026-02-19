.. code-block:: json

    {
      "ads": [
        {
          // ...
          "price": {
            "amountCents": 5600,
            "originalAmountCents": 6500,
            "priceType": "FIXED_PRICE"
          },
          "campaignId": 54212,
          "bidMicros": "10000",
          "budgets": {
            "daily": {
              "limitMicros": "UNLIMITED",
              "spentMicros": "500000"
            },
            "total": {
              "limitMicros": "10000000",
              "spentMicros": "1200000"
            }
          },
          "shippingOptions": [
            {
              "costCents": 500,
              "time": "2d-5d"
            }
          ]
        }
      ],
      "count": 1
    }

