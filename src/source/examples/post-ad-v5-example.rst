.. code-block:: javascript

    POST /ad
    Accept: application/sellside.ad-v5+json, application/json
    Content-Type: application/sellside.ad-v5+json; charset=utf-8

    {
        "title": "Brother Fax voor 99,99",
        "description": "<b>NU extra voordelig op ourshop.com.</b> Fax nu voor slechts <b>99,99!</b>",
        "categoryId": 826,
        "externalId": "OURSHOP-1423453-34",
        "status": "ACTIVE",
        "currency": "EUR",
        "priceType": "FIXED_PRICE",
        "priceUnit": "per_sqm",
        "price": 9999,
        "salutation": "COMPANY",
        "sellerName": "My Shop",
        "postcode": "1097DN",
        "regionId": 1700195,
        "phoneNumber": "0207894561",
        "allowContactByEmail": true,
        "allowPaypal": true,
        "links": {
            "url": "http://www.ourshop.com/index.php?param1=value1&amp;param2=value2&amp;param3=value3",
            "displayUrl": "www.ourshop.com/Faxes"
        },
        "images": [
            {
                "src": "http://images.ourshop.com/source1.jpg"
            },
            {
                "src": "http://images.ourshop.com/source2.jpg"
            },
            {
                "src": "http://images.ourshop.com/source3.jpg"
            }
        ],
        "attributes": [
            {
                "key": "color",
                "label": "Kleur",
                "locale": "nl_NL",
                "type": "STRING",
                "value": "Zwart"
            },
            {
                "key": "color",
                "label": "Color",
                "locale": "en_US",
                "type": "STRING",
                "value": "Black"
            },
            {
                "key": "size",
                "label": "Maat",
                "locale": "nl_NL",
                "type": "NUMBER",
                "value": 6
            },
            {
                "key": "software",
                "label": "Software",
                "type": "LIST",
                "locale": "nl_NL",
                "value": [
                    "Apple OSX",
                    "Microsoft Windows 7"
                ]
            }
        ],
        "shippingOptions": [
            {
                "type": "SHIP",
                "cost": 0,
                "time": "2d-5d"
            },
            {
                "type": "PICKUP",
                "pickupLocation": "1097DN"
            }
        ],
        "paypalEmail": "test@example.com"
    }