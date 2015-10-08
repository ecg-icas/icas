.. code-block:: javascript

    GET /api/sellside/region?levels=1&_include=&_exclude=
    Accept: application/sellside.region-v1+json, application/json

    200 OK
    Content-Type: application/sellside.region-v1+json; charset=utf-8

    {
        "links": {
            "self": "/api/sellside/region/0"
        },
        "id": 0,
        "parentId": 0,
        "level": 0,
        "path": "",
        "label": {
            "en_CA": "Canada",
            "fr_CA": "Canada"
        },
        "children": [
            {
                "links": {
                    "self": "/api/sellside/region/9009"
                },
                "id": 9009,
                "parentId": 0,
                "level": 1,
                "path": "9009",
                "label": {
                    "en_CA": "Saskatchewan",
                    "fr_CA": "Saskatchewan"
                }
            },
            {
                "links": {
                    "self": "/api/sellside/region/9010"
                },
                "id": 9010,
                "parentId": 0,
                "level": 1,
                "path": "9010",
                "label": {
                    "en_CA": "Territories",
                    "fr_CA": "Territoires"
                }
            },
            {
                "links": {
                    "self": "/api/sellside/region/9011"
                },
                "id": 9011,
                "parentId": 0,
                "level": 1,
                "path": "9011",
                "label": {
                    "en_CA": "Prince Edward Island",
                    "fr_CA": "L'Île-du-Prince-Édouard"
                }
            },
            {
                "links": {
                    "self": "/api/sellside/region/9001"
                },
                "id": 9001,
                "parentId": 0,
                "level": 1,
                "path": "9001",
                "label": {
                    "en_CA": "Québec",
                    "fr_CA": "Québec"
                }
            },
            {
                "links": {
                    "self": "/api/sellside/region/9002"
                },
                "id": 9002,
                "parentId": 0,
                "level": 1,
                "path": "9002",
                "label": {
                    "en_CA": "Nova Scotia",
                    "fr_CA": "Nouvelle-Écosse"
                }
            },
            {
                "links": {
                    "self": "/api/sellside/region/9003"
                },
                "id": 9003,
                "parentId": 0,
                "level": 1,
                "path": "9003",
                "label": {
                    "en_CA": "Alberta",
                    "fr_CA": "Alberta"
                }
            },
            {
                "links": {
                    "self": "/api/sellside/region/9004"
                },
                "id": 9004,
                "parentId": 0,
                "level": 1,
                "path": "9004",
                "label": {
                    "en_CA": "Ontario",
                    "fr_CA": "Ontario"
                }
            },
            {
                "links": {
                    "self": "/api/sellside/region/9005"
                },
                "id": 9005,
                "parentId": 0,
                "level": 1,
                "path": "9005",
                "label": {
                    "en_CA": "New Brunswick",
                    "fr_CA": "Nouveau-Brunswick"
                }
            },
            {
                "links": {
                    "self": "/api/sellside/region/9006"
                },
                "id": 9006,
                "parentId": 0,
                "level": 1,
                "path": "9006",
                "label": {
                    "en_CA": "Manitoba",
                    "fr_CA": "Manitoba"
                }
            },
            {
                "links": {
                    "self": "/api/sellside/region/9007"
                },
                "id": 9007,
                "parentId": 0,
                "level": 1,
                "path": "9007",
                "label": {
                    "en_CA": "British Columbia",
                    "fr_CA": "Colombie-Britannique"
                }
            },
            {
                "links": {
                    "self": "/api/sellside/region/9008"
                },
                "id": 9008,
                "parentId": 0,
                "level": 1,
                "path": "9008",
                "label": {
                    "en_CA": "Newfoundland",
                    "fr_CA": "Terre-Neuve"
                }
            }
        ]
    }
