.. code-block:: javascript

    POST /ad
    Accept: application/sellside.ad-v5+json, application/json
    Content-Type: application/sellside.ad-v5+json; charset=utf-8

    {
        "title": "Brother Fax voor 99,99",
        "description": "<b>NU extra voordelig op ourshop.com.</b> Fax nu voor slechts <b>99,99!</b>",
        "categoryId": 826,
        "status": "ACTIVE",
        "price": {
            "priceType": "FIXED_PRICE",
            "priceUnit": "per_sqm",
            "amountCents": 5600,
            "originalAmountCents": 6500
        },
        "bidMicros": "AUTOMATIC",
        "budgets": {
            "daily": {
                "limitMicros": "30000000",
            },
            "total": {
                "limitMicros": "UNLIMITED",
            }
        },
        "campaignId": 54212,
        "salutation": "COMPANY",
        "sellerName": "My Shop",
        "postcode": "1097DN",
        "regionId": 1700195,
        "phoneNumber": "0207894561",
        "allowContactByEmail": true,
        "vendorId": "OURSHOP-1423453-34",
        "links": {
            "displayUrl": "www.ourshop.com/Faxes",
            "url": "http://www.ourshop.com/index.php?param1=value1&amp;param2=value2&amp;param3=value3"
        },
        "images": [
            {
                "src": "http://www.ourshop.com/img/brother_fax_big.jpg",
            },
            {
                "src": "http://www.ourshop.com/img/brother_fax_side.jpg",
            }
        ],
        "attributes": [
            {
                "key": "color",
                "label": "Kleur",
                "locale": "nl",
                "type": "STRING",
                "value": "Zwart",
            },
            {
                "key": "size",
                "label": "Maat",
                "locale": "nl",
                "type": "NUMBER",
                "value": 6,
            },
            {
                "key": "software",
                "label": "Software",
                "locale": "nl",
                "type": "LIST",
                "value": [
                    "Apple OSX",
                    "Microsoft Windows 7"
                ],
            }
        ],
        "shippingOptions": [
            {
                "type": "SHIP",
                "costCents": 495,
                "time": "2d-5d"
            },
            {
                "type": "PICKUP",
                "pickupLocation": "1097DN"
            }
        ]
    }