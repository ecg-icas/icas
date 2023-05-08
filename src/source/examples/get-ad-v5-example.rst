.. code-block:: javascript

    GET /ad[?limit=limit][&pageToken=eyJpZCI6MTAwMT....][&orderBy=orderBy][&titleKeywords=titleKeywords][&status=Status][&changedSince=timestamp][&remainingBudget=number[%]][&_include=list,of,fields][&_exclude=list,of,fields][&adIds=123,456,457][&campaignId=6531][&startDate=2014-12-04][&endDate=2015-06-13]
    Accept: application/sellside.ad.list-v5+json, application/json

    200 OK
    Content-Type: application/sellside.ad.list-v5+json; charset=utf-8

    {
      "ads": [
        {
          "id": 42,
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
          "bidMicros": "10000",
          "budgets": {
            "daily": {
              "limitMicros": "UNLIMITED",
              "spentMicros": "1255000"
            },
            "total": {
              "limitMicros": "350000000",
              "spentMicros": "24370000"
            }
          },
          "salutation": "COMPANY",
          "sellerName": "My Shop",
          "postcode": "1097DN",
          "regionId": 1700195,
          "phoneNumber": "0207894561",
          "allowContactByEmail": true,
          "dateCreated": "2012-08-31T16:12:53Z",
          "dateLastUpdated": "2012-09-05T04:03:42Z",
          "vendorId": "OURSHOP-1423453-34",
          "links": {
            "self": "/ad/42",
            "category": "/category/826",
            "displayUrl": "www.ourshop.com/Faxes",
            "url": "http://www.ourshop.com/index.php?param1=value1&amp;param2=value2&amp;param3=value3"
          },
          "images": [
            {
              "src": "http://www.ourshop.com/img/brother_fax_big.jpg",
              "status": "OK",
              "dateLastUpdated": "2012-09-10T13:11:05Z",
              "links": {
                "50x70": "//i.marktplaats.nl/image23434_abc.jpg",
                "120x180": "//i.marktplaats.nl/image23434_def.jpg"
              }
            },
            {
              "src": "http://www.ourshop.com/img/brother_fax_side.jpg",
              "status": "OK",
              "dateLastUpdated": "2012-09-10T13:11:05Z",
              "links": {
                "50x70": "//i.marktplaats.nl/image397493_abc.jpg",
                "120x180": "//i.marktplaats.nl/image397493_def.jpg"
              }
            }
          ],
          "attributes": [
            {
              "key": "color",
              "label": "Kleur",
              "locale": "nl",
              "type": "STRING",
              "value": "Zwart",
              "recognized": true
            },
            {
              "key": "size",
              "label": "Maat",
              "locale": "nl",
              "type": "NUMBER",
              "value": 6,
              "recognized": true
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
              "recognized": false
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
      ],
      "count": 4,
      "nextPageToken": "eyJpZCI6MTAwMTgzMTc1MCwic3RyaW5nX3ZhbHVlIjpudWxsLCJpbnQ2NF92YWx1ZSI6MTM0MDIxNzg1OTc5MH0"
    }
