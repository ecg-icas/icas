.. code-block:: javascript

    GET /api/sellside/category/2?levels=1
    Accept: application/sellside.category-v5+json; application/json

    200 OK
    Content-Type: application/sellside.category-v5+json; charset=utf-8

    {
      "links": {
        "parent": "/api/sellside/category/856",
        "self": "/api/sellside/category/863"
      },
      "id": 863,
      "parentId": 856,
      "level": 2,
      "path": "856_863",
      "label": {
        "nl_NL": "Vakantiehuizen | Duitsland"
      },
      "breadcrumbs": {
        "nl_NL": [
          "Vakantie",
          "Vakantiehuizen | Duitsland"
        ]
      },
      "status": "ACTIVE",
      "config": {
        "bidMicros": "[10000,2500000]",
        "totalBudgetMicros": "[5000000,200000000000]",
        "dailyBudgetMicros": "[1000000,200000000000]",
        "activeAds": "[0,7000]",
        "titleLength": "[1,60]",
        "descriptionLength": "[1,20000]",
        "images": "[1,24]",
        "urlMandatory": false,
        "shippingOption": "DISABLED",
        "priceTypes": ["FIXED_PRICE", "BIDDING_FROM", "SEE_DESCRIPTION"],
        "priceUnits": {
          "per_night": {
            "nl_NL": "per nacht"
          }
        },
        "verticals": [
          "VACATIONS"
        ],
        "tags": {
          "nl_NL": [
            "vakantiehuis"
          ]
        },
        "relatedPaths": [
          "856_892",
          "856_862"
        ]
      },
      "attributeGroups": [
        {
          "label": {
            "nl_NL": "Kenmerken"
          },
          "tooltip": {
            "nl_NL": "Geef hier welk type advertentie u gaat maken en wat de conditie van uw product is"
          },
          "attributes": [
            {
              "key": "region",
              "label": {
                "nl_NL": "Regio"
              },
              "tooltip": {},
              "type": "STRING",
              "values": {
                "nl_NL": [
                 "Sauerland",
                 "Beieren",
                 "Berlijn",
                 "Eifel",
                 "Harz",
                 "Moezel",
                 "Noord-Duitsland",
                 "Oost-Duitsland",
                 "Zwarte Woud",
                 "Overige regio's"
                  ]
                },
                "defaults": {},
                "mandatory": false,
                "searchable": true,
                "updatable": true,
                "writable": true,
                "precision": 0,
                "range": null,
                "length": null,
                "prefix": {},
                "postfix": {},
                "hints": []
              },
              {
                "key": "type",
                "label": {
                  "nl_NL": "Type"
                },
                "tooltip": {},
                "type": "STRING",
                "values": {
                  "nl_NL": [
                    "Appartement",
                    "Boerderij of Cottage",
                    "Chalet, Bungalow of Caravan",
                    "Landhuis of Villa",
                    "Overige typen"
                  ]
                },
                "defaults": {},
                "mandatory": false,
                "searchable": true,
                "updatable": true,
                "writable": true,
                "precision": 0,
                "range": null,
                "length": null,
                "prefix": {},
                "postfix": {},
                "hints": []
              },
              {
                "key": "numberOfBedrooms",
                "label": {
                  "nl_NL": "Aantal slaapkamers"
                },
                "tooltip": {},
                "type": "STRING",
                "values": {
                   "nl_NL": [
                     "1 slaapkamer",
                     "2 slaapkamers",
                     "3 slaapkamers",
                     "4 of meer slaapkamers",
                     "Groepsaccommodatie"
                   ]
                 },
                 "defaults": {},
                 "mandatory": false,
                 "searchable": true,
                 "updatable": true,
                 "writable": true,
                 "precision": 0,
                 "range": null,
                 "length": null,
                 "prefix": {},
                 "postfix": {},
                 "hints": []
              },
              {
                "key": "numberOfPersons",
                "label": {
                  "nl_NL": "Aantal personen"
                },
                "tooltip": {},
                "type": "NUMBER",
                "values": {},
                "defaults": {},
                "mandatory": false,
                "searchable": true,
                "updatable": true,
                "writable": true,
                "precision": 0,
                "range": "[1,99]",
                "length": null,
                "prefix": {},
                "postfix": {
                    "nl_NL": "personen"
                },
                "hints": []
              }
            ]
          }
        ]
    }
