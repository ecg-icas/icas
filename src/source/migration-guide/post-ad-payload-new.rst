.. code-block:: json

    {
      // ...
      "price": {
        "amountCents": 5600,
        "originalAmountCents": 6500,
        "priceType": "FIXED_PRICE"
      },
      "vendorId": "OUR-SHOP-123",
      "bidMicros": "10000",
      "budgets": {
        "daily": {
          "limitMicros": "UNLIMITED",
        },
        "total": {
          "limitMicros": "10000000",
        }
      },
      "shippingOptions": [
        {
          "costCents": 500,
          "time": "2d-5d"
        }
      ]
    }
