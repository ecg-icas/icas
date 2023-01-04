.. code-block:: javascript

    GET /api/sellside/feed/import/123/detail
    Accept: application/sellside.feedimportdetail-v2+json; application/json

    200 OK HTTP/1.1
    Content-Type: application/sellside.feedimportdetail-v2+json; charset=UTF-8

    {
        "id": 123,
        "url": "http://feed.com/id/5324.xml",
        "dateCreated": "2021-08-31T16:12:53Z",
        "status": "REJECTED",
        "error": "HTTP 404 Not Found for: http://feed.com/id/5324.xml: fetch url failure",
        "totalCount": 0,
        "okCount": 0,
        "errorCount": 0,
        "warningCount": 0,
        "errors": {},
        "warnings": {}
    }
