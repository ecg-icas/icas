.. code-block:: javascript

    GET /api/sellside/campaign/234234/views/performance?categoryIds=1340,1350&type=HighSpend&limit=5
    Accept: application/sellside.ad-lite.list-v1+json

    404 Not found
    Content-Type: application/json; charset=utf-8

    [
        {
            "code": 1004,
            "text": "not found",
            "msg": "The entity was not found",
            "field": "campaignID",
            "arg": "234234"
        }
    ]


.. code-block:: javascript

    GET /api/sellside/campaign/549/views/performance?categoryIds=blah123&limit=5
    Accept: application/sellside.ad-lite.list-v1+json

    400 Bad Request
    Content-Type: application/json; charset=utf-8

    [
        {
            "code": 2001,
            "text": "invalid argument",
            "msg": "The value of field 'categoryIds' was invalid",
            "field": "categoryIds",
            "arg": "blah123"
        }
    ]


.. code-block:: javascript

    GET /api/sellside/campaign/549/views/performance?limit=500
    Accept: application/sellside.ad-lite.list-v1+json

    400 Bad Request
    Content-Type: application/json; charset=utf-8

    [
        {
            "code": 2002,
            "text": "out of range",
            "msg": "The value of the field 'limit' was out of range ( limit > 100 or < 1)",
            "field": "limit",
            "arg": "limit > 100 or < 1"
        }
    ]


.. code-block:: javascript

    GET /api/sellside/campaign/549/views/performance?categoryIds=1340,1350&limit=5&type=someType
    Accept: application/sellside.ad-lite.list-v1+json

    400 Bad Request
    Content-Type: application/json; charset=utf-8

    [
        {
            "code": 2001,
            "text": "invalid argument",
            "msg": "The value of field 'type' was invalid",
            "field": "type",
            "arg": "sometype"
        }
    ]


.. code-block:: javascript

    GET /api/sellside/campaign/549/views/performance?startDate=2021-01-31&endDate=2020-02-20
    Accept: application/sellside.ad-lite.list-v1+json

    400 Bad Request
    Content-Type: application/json; charset=utf-8

    [
        {
            "code": 2001,
            "text": "invalid argument",
            "msg": "The value of field 'endDate' was invalid",
            "field": "endDate",
            "arg": "2020-02-20"
        }
    ]
