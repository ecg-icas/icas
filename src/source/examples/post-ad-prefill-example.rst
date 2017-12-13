.. code-block:: javascript

    POST /api/sellside/ad/prefill
    Accept: application/sellside.ad.template-v1+json
    Content-Type: application/sellside.ad.template-v1+json; charset=utf-8

    {
      "categoryId": 85,
      "attributes":[
        {
          "key": "licensePlate",
          "label": "License Plate",
          "locale": "nl",
          "type": "STRING",
          "value": "1CAS23"
        }
      ]
    }

    200 OK
    Content-Type: application/sellside.ad.template-v1+json; charset=utf-8

    {
      "title":"Citroen C5 2.0 HDI 81KW Break 2004 Grijs",
      "description":"",
      "categoryId": 133,
      "attributes":[
        {
          "key": "color",
          "label": "Kleur",
          "locale": "nl",
          "type": "STRING",
          "value": "Zilver of Grijs",
          "recognized": true
        },
        {
          "key": "body",
          "label": "Carrosserie",
          "locale": "nl",
          "type": "STRING",
          "value": "Stationwagon",
          "recognized": true
        }
      ]
    }