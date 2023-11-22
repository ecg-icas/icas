.. code-block:: javascript

    GET /api/sellside/categories?_traceId=api-test-672698259&categoryIds=1%2C2%2C22 HTTP/1.1

    Host: www.mp.test
    Authorization: Bearer d66d0344-143d-4cd2-9b62-789c85e536fe
    Accept: application/sellside.category.list-v5+json; application/json
    
    200 OK HTTP/1.1
    Content-Type: application/sellside.category.list-v5+json
    Oauth-Scope: api_ro api_rw console_ro console_rw
    Oauth-Scope-Required: get_category

    {
      "1": {
        "links": {
          "self": "/api/sellside/category/1",
          "parent": "/api/sellside/category/0"
        },
        "id": 1,
        "parentId": 0,
        "level": 1,
        "path": "1",
        "locales": [
          "nl_NL"
        ],
        "label": {
          "nl_NL": "Antiek en Kunst"
        },
        "breadcrumbs": {
          "nl_NL": [
            "Antiek en Kunst"
          ]
        },
        "status": "ACTIVE",
        "children": []
      },
      "2": {
        "links": {
          "self": "/api/sellside/category/2",
          "parent": "/api/sellside/category/1"
        },
        "id": 2,
        "parentId": 1,
        "level": 2,
        "path": "1_2",
        "locales": [
          "nl_NL"
        ],
        "label": {
          "nl_NL": "Antiek | Bestek"
        },
        "breadcrumbs": {
          "nl_NL": [
            "Antiek en Kunst",
            "Antiek | Bestek"
          ]
        },
        "status": "ACTIVE",
        "config": {
          "bidMicros": "[10000,2500000]",
          "totalBudgetMicros": "[1000000,2000000000000]",
          "dailyBudgetMicros": "[10000000,2000000000000]",
          "activeAds": "[1,100000]",
          "titleLength": "[1,60]",
          "descriptionLength": "[1,20000]",
          "images": "[0,24]",
          "urlMandatory": false,
          "shippingOption": "OPTIONAL",
          "priceTypes": [
            "BIDDING",
            "BIDDING_FROM",
            "FIXED_PRICE",
            "FREE",
            "NEGOTIABLE",
            "SEE_DESCRIPTION",
            "SWAP",
            "CREDIBLE_BID",
            "ON_DEMAND",
            "NOT_APPLICABLE",
            "RESERVED"
          ],
          "priceUnits": {},
          "verticals": [],
          "tags": {},
          "region": "DISABLED",
          "relatedPaths": [
            "1_2614",
            "1_15",
            "504_1941"
          ]
        },
        "attributeGroups": [{
          "label": {
            "nl_NL": "Kenmerken"
          },
          "tooltip": {
            "nl_NL": "Geef hier welk type advertentie u gaat maken en wat de conditie van uw product is"
          },
          "attributes": []
        }],
        "children": []
      },
      "22": {
        "links": {
          "self": "/api/sellside/category/22",
          "parent": "/api/sellside/category/1826"
        },
        "id": 22,
        "parentId": 1826,
        "level": 2,
        "path": "1826_22",
        "locales": [
          "nl_NL"
        ],
        "label": {
          "nl_NL": "Ringen"
        },
        "breadcrumbs": {
          "nl_NL": [
            "Sieraden, Tassen en Uiterlijk",
            "Ringen"
          ]
        },
        "status": "ACTIVE",
        "config": {
          "bidMicros": "[20000,2500000]",
          "totalBudgetMicros": "[50000000,2000000000000]",
          "dailyBudgetMicros": "[10000000,2000000000000]",
          "activeAds": "[1,100000]",
          "titleLength": "[1,60]",
          "descriptionLength": "[1,20000]",
          "images": "[0,24]",
          "urlMandatory": false,
          "shippingOption": "OPTIONAL",
          "priceTypes": [
            "BIDDING",
            "BIDDING_FROM",
            "FIXED_PRICE",
            "FREE",
            "NEGOTIABLE",
            "SEE_DESCRIPTION",
            "SWAP",
            "CREDIBLE_BID",
            "ON_DEMAND",
            "NOT_APPLICABLE",
            "RESERVED"
          ],
          "priceUnits": {},
          "verticals": [],
          "tags": {
            "nl_NL": [
              "Ring"
            ]
          },
          "region": "DISABLED",
          "relatedPaths": [
            "1826_1827",
            "1826_18",
            "1826_13",
            "1826_19",
            "621_625"
          ]
        },
        "attributeGroups": [{
          "label": {
            "nl_NL": "Kenmerken"
          },
          "tooltip": {
            "nl_NL": "Geef hier welk type advertentie u gaat maken en wat de conditie van uw product is"
          },
          "attributes": [
            {
              "key": "condition",
              "label": {
                "nl_NL": "Conditie"
              },
              "tooltip": {},
              "type": "STRING",
              "values": {
                "nl_NL": [
                  "Nieuw",
                  "Zo goed als nieuw",
                  "Gebruikt"
                ]
              },
              "defaults": {
                "nl_NL": "Nieuw"
              },
              "mandatory": false,
              "searchable": true,
              "updatable": true,
              "writable": true,
              "precision": 0,
              "range": null,
              "length": null,
              "prefix": {},
              "postfix": {},
              "hints": [],
              "identifying": false
            },
            {
              "key": "intendedFor",
              "label": {
                "nl_NL": "Bestemd voor"
              },
              "tooltip": {},
              "type": "STRING",
              "values": {
                "nl_NL": [
                  "Dame",
                  "Heer",
                  "Dame of Heer"
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
              "hints": [],
              "identifying": false
            },
            {
              "key": "size",
              "label": {
                "nl_NL": "Maat"
              },
              "tooltip": {},
              "type": "STRING",
              "values": {
                "nl_NL": [
                  "Kleiner dan 17",
                  "17 tot 18",
                  "18 tot 19",
                  "19 tot 20",
                  "20 of groter"
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
              "hints": [],
              "identifying": false
            },
            {
              "key": "color",
              "label": {
                "nl_NL": "Kleur"
              },
              "tooltip": {},
              "type": "STRING",
              "values": {
                "nl_NL": [
                  "Blauw",
                  "Rood",
                  "Wit",
                  "Zwart",
                  "Beige",
                  "Bruin",
                  "Geel",
                  "Goud",
                  "Grijs",
                  "Groen",
                  "Oranje",
                  "Paars",
                  "Roze",
                  "Zilver",
                  "Overige kleuren"
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
              "hints": [],
              "identifying": false
            },
            {
              "key": "material",
              "label": {
                "nl_NL": "Materiaal"
              },
              "tooltip": {},
              "type": "STRING",
              "values": {
                "nl_NL": [
                  "Goud",
                  "Zilver",
                  "IJzer of Staal",
                  "Kunststof",
                  "Overige materialen"
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
              "hints": [],
              "identifying": false
            }
          ]
        }],
        "children": []
      }
    }