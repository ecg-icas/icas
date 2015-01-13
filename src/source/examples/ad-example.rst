.. code-block:: javascript

   GET /ad/42
   Accept: application/sellside.ad-v1+json, application/json

   200 OK
   Content-Type: application/sellside.ad-v1+json;charset=UTF-8

   {
        "id": 42,
        "title": "Brother Fax voor 99,99",
        "description": "<b>NU extra voordelig op ourshop.com.</b> Fax nu voor slechts <b>99,99!</b>",
        "categoryId": 826,
        "externalId": "OURSHOP-1423453-34",
        "status": "ACTIVE",
        "currency": "EUR",
        "priceType": "FIXED_PRICE",
        "price": 9999,
        "cpc": 10,
        "totalBudget": 5000,
        "dailyBudget": 2000,
        "spentBudget": 2534,
        "salutation": "COMPANY",
        "sellerName": "My Shop",
        "postcode": "1097DN",
        "pageNumber": 27,
        "suggestedCpcForPageOne": 74,
        "phoneNumber": "0207894561",
        "allowContactByEmail": true,
        "dateCreated" : "2012-08-31T16:12:53Z",
        "dateLastUpdated" : "2012-09-05T04:03:42Z",
        "links": {
            "self" : "/ad/42",
            "category" : "/category/826",
            "displayUrl" : "www.ourshop.com/Faxes",
            "url" : "http://www.ourshop.com/index.php?param1=value1&amp;param2=value2&amp;param3=value3",
       },
       "images": [
            {
                "src": "http://www.ourshop.com/img/brother_fax_big.jpg",
                "status": "OK",
                "dateLastUpdated": "2012-09-10T13:11:05Z",
                "links": {
                    "50x70": "http://i.marktplaats.nl/image23434_abc.jpg",
                    "120x180": "http://i.marktplaats.nl/image23434_def.jpg",
                }
            },
            {
                "src": "http://www.ourshop.com/img/brother_fax_side.jpg",
                "status": "OK",
                "dateLastUpdated": "2012-09-10T13:11:05Z",
                "links": {
                    "50x70": "http://i.marktplaats.nl/image397493_abc.jpg",
                    "120x180": "http://i.marktplaats.nl/image397493_def.jpg",
                }
            }
       ],
       "attributes": [
            {
                "key" : "Kleur",
                "label" : "Kleur",
                "locale" : "nl",
                "type": "STRING",
                "value" : "Zwart",
                "recognized" : true
            },
            {
                "key" : "Maat",
                "label" : "Maat",
                "locale" : "nl",
                "type" : "NUMBER",
                "value" : 6,
                "recognized" : true
            },
            {
                "key" : "Software",
                "label" : "Software",
                "locale" : "nl",
                "type" : "LIST",
                "value": ["Apple OSX","Microsoft Windows 7"],
                "recognized" : false
            }

       ],
       "shippingOptions": [
            {
                "type": "SHIP",
                "cost": 0,
                "time":"2d-5d"
            },
            {
                "type": "PICKUP",
                "pickupLocation":"1097DN"
            }
       ],
       "paypalEmail" : "test@example.com"
   }
