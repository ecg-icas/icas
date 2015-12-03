.. code-block:: javascript

    GET /ad[?limit=limit][&offset=offset][&titleKeywords=titleKeywords][&status=Status][&orderBy=orderBy][&changedSince=timestamp][&remainingBudget=number[%]][&_include=list,of,fields][&_exclude=list,of,fields][&startDate=2014-12-04][&endDate=2015-06-13]
    Accept: application/sellside.ad.list-v2+json, application/json

    200 OK
    Content-Type: application/sellside.ad.list-v3+json; charset=utf-8

    {
      "ads": [
        {
          "links": {
            "category": "/api/sellside/category/453",
            "self": "/api/sellside/ad/3000000604"
          },
          "id": 3000000604,
          "title": "Franks fiets",
          "description": "mijn fiets",
          "categoryId": 453,
          "externalId": "79fb0210-f53c-4663-83c4-6f9de776e98b",
          "currency": "EUR",
          "priceType": "FIXED_PRICE",
          "price": 12300,
          "cpc": 7,
          "totalBudget": 10000,
          "spentBudget": 0,
          "salutation": "COMPANY",
          "sellerName": "Test schildersbedrijf",
          "phoneNumber": "0612345678",
          "allowContactByEmail": true,
          "allowPaypal": false,
          "status": "ACTIVE",
          "postcode": "1011DK",
          "pageNumber": 1,
          "suggestedCpcForPageOne": 5,
          "dateCreated": "2015-06-15T15:06:08Z",
          "dateLastUpdated": "2015-06-15T15:06:08Z",
          "vendorId": "OURSHOP-1423453-34",
          "attributes": [
            {
              "key": "condition",
              "label": "Conditie",
              "locale": "nl",
              "type": "STRING",
              "value": "Nieuw",
              "recognized": true
            },
            {
              "key": "brand",
              "label": "Merk",
              "locale": "nl",
              "type": "STRING",
              "value": "Gazelle",
              "recognized": true
            },
            {
              "key": "frameHeight",
              "label": "Framehoogte",
              "locale": "nl",
              "type": "STRING",
              "value": "57 tot 61 cm",
              "recognized": true
            },
            {
              "key": "properties",
              "label": "Eigenschappen",
              "locale": "nl",
              "type": "LIST",
              "value": [
                "Versnellingen"
              ],
              "recognized": true
            }
          ],
          "images": [],
          "shippingOptions": []
        }
      ],
      "count": 1
    }