.. code-block:: javascript

    GET /api/sellside/regions?regionIds=1700093,1700195,1700196 HTTP/1.1
    Accept: application/sellside.region.list-v1+json; application/json

    200 OK HTTP/1.1
    Content-Length: 808
    Content-Type: application/sellside.region.list-v1+json; charset=UTF-8
    Date: Fri, 02 Sep 2016 14:00:35 GMT
    Oauth-Scope: api_ro api_rw
    Oauth-Scope-Required: get_region

    {
        "1700093": {
            "links": {
                "parent": "/api/sellside/region/9009",
                "self": "/api/sellside/region/1700093"
            },
            "id": 1700093,
            "parentId": 9009,
            "level": 2,
            "path": "9009_1700093",
            "center": {
                "latitude": 50.283,
                "longitude": -107.767
            },
            "label": {
                "en_CA": "Swift Current",
                "fr_CA": "Swift Current"
            }
        },
        "1700195": {
            "links": {
                "parent": "/api/sellside/region/1700194",
                "self": "/api/sellside/region/1700195"
            },
            "id": 1700195,
            "parentId": 1700194,
            "level": 3,
            "path": "9009_1700194_1700195",
            "center": {
                "latitude": 50.4,
                "longitude": -105.55
            },
            "label": {
                "en_CA": "Moose Jaw",
                "fr_CA": "Moose Jaw"
            }
        },
        "1700196": {
            "links": {
                "parent": "/api/sellside/region/1700194",
                "self": "/api/sellside/region/1700196"
            },
            "id": 1700196,
            "parentId": 1700194,
            "level": 3,
            "path": "9009_1700194_1700196",
            "center": {
                "latitude": 50.448009,
                "longitude": -104.595177
            },
            "label": {
                "en_CA": "Regina",
                "fr_CA": "Regina"
            }
        }
    }