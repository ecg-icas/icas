.. code-block:: javascript

    GET /api/sellside/campaign/234234/views/status?categoryIds=1340,1350&type=inactive&limit=5
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

    GET /api/sellside/campaign/549/views/status?categoryIds=blah123&limit=5
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

    GET /api/sellside/campaign/549/views/status?limit=500
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

    GET /api/sellside/campaign/549/views/status?categoryIds=1340,1350&limit=5&type=someType
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

    GET /api/sellside/campaign/549/views/status?pageToken=blaah&limit=5&type=inactive
    Accept: application/sellside.ad-lite.list-v1+json

    400 Bad Request
    Content-Type: application/json; charset=utf-8

    [
        {
            "code": 2001,
            "text": "invalid argument",
            "msg": "The value of field 'pageToken' was invalid",
            "field": "pageToken",
            "arg": "blaah"
        }
    ]


.. warning::

    If the number of ads filtered by applying the ``categoryIds`` or ``regionIds`` filter(s) is greater than 5000 (regardless of the ``limit`` parameter), a server error is returned.
    This is an internal technical restriction that we hope to be able to lift in the future.


.. code-block:: javascript

    GET /api/sellside/campaign/549/views/status?categoryIds=1340,1350&type=inactive&limit=5
    Accept: application/sellside.ad-lite.list-v1+json

    507 "Insufficient Storage"
    Content-Type: application/json; charset=utf-8

    [
        {
            "status": 507,
            "message": "Maximum number of data points required to compute the result exceeded"
        }
    ]
