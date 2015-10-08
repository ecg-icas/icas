.. code-block:: javascript

    GET /api/sellside/categories?categoryIds=863,431
    Accept: application/sellside.category.list-v1+json; application/json

    200 OK
    Content-Type: application/sellside.category.list-v1+json; charset=utf-8

    {
        "431": {
            "links": {
                "parent": "/api/sellside/category/428",
                "self": "/api/sellside/category/431"
            },
            "id": 431,
            "parentId": 428,
            "level": 2,
            "path": "428_431",
            "locales": [
                "nl_NL"
            ],
            "label": {
                "nl_NL": "Zorg | Brommobielen en Scootmobielen"
            },
            "breadcrumbs": {
                "nl_NL": [
                    "Diversen",
                    "Zorg | Brommobielen en Scootmobielen"
                ]
            },
            "status": "ACTIVE",
            "config": {
                "cpc": "[1,250]",
                "totalBudget": "[5000,200000000]",
                "minDailyBudget": 1000,
                "activeAds": "[1,7000]",
                "titleLength": "[1,60]",
                "descriptionLength": "[1,20000]",
                "images": "[0,8]",
                "urlMandatory": false,
                "shippingOption": "DISABLED",
                "paypalEnabled": true,
                "paypalBpEnabled": false,
                "currency": "EUR",
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
                    "RESERVED"
                ],
                "priceUnits": {},
                "verticals": [],
                "tags": {},
                "region": "DISABLED",
                "relatedPaths": [
                    "445_712",
                    "91_157"
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
                            "mandatory": true,
                            "searchable": true,
                            "updatable": true,
                            "writable": true,
                            "precision": 0,
                            "range": null,
                            "length": null,
                            "prefix": {},
                            "postfix": {},
                            "hints": []
                        }
                    ]
                }
            ]
        },
        "863": {
            "links": {
                "parent": "/api/sellside/category/856",
                "self": "/api/sellside/category/863"
            },
            "id": 863,
            "parentId": 856,
            "level": 2,
            "path": "856_863",
            "locales": [
                "nl_NL"
            ],
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
                "cpc": "[1,250]",
                "totalBudget": "[5000,200000000]",
                "minDailyBudget": 1000,
                "activeAds": "[1,7000]",
                "titleLength": "[1,60]",
                "descriptionLength": "[1,20000]",
                "images": "[0,8]",
                "urlMandatory": false,
                "shippingOption": "DISABLED",
                "paypalEnabled": true,
                "paypalBpEnabled": false,
                "currency": "EUR",
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
                    "RESERVED"
                ],
                "priceUnits": {},
                "verticals": [
                    "VACATIONS"
                ],
                "tags": {
                    "nl_NL": [
                        "vakantiehuis"
                    ]
                },
                "region": "DISABLED",
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
                            "key": "situated",
                            "label": {
                                "nl_NL": "Ligging"
                            },
                            "tooltip": {},
                            "type": "STRING",
                            "values": {
                                "nl_NL": [
                                    "Dorp",
                                    "Stad",
                                    "Landelijk",
                                    "Recreatiepark",
                                    "Overige"
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
                            "key": "surroundings",
                            "label": {
                                "nl_NL": "Omgeving"
                            },
                            "tooltip": {},
                            "type": "LIST",
                            "values": {
                                "nl_NL": [
                                    "Aan zee",
                                    "Aan meer of rivier",
                                    "In bergen of heuvels",
                                    "In bos",
                                    "In wintersportgebied"
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
                            "key": "letter",
                            "label": {
                                "nl_NL": "Verhuurder"
                            },
                            "tooltip": {},
                            "type": "STRING",
                            "values": {
                                "nl_NL": [
                                    "Eigenaar",
                                    "Bemiddelingsbureau"
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
                            "key": "extras",
                            "label": {
                                "nl_NL": "Extra's"
                            },
                            "tooltip": {},
                            "type": "LIST",
                            "values": {
                                "nl_NL": [
                                    "Afwasmachine",
                                    "Airconditioning",
                                    "Huisdier toegestaan",
                                    "Internet",
                                    "Kinderbed",
                                    "Open haard",
                                    "Rolstoelvriendelijk",
                                    "Sauna of Jaccuzi",
                                    "Speeltuin",
                                    "Tuin",
                                    "Tv",
                                    "Wasmachine",
                                    "Zwembad"
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
    }