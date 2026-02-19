.. code-block:: javascript

    GET /api/sellside/feed/import
    Accept: application/sellside.feedimport.list-v1+json; application/json

    200 OK
    Content-Type: application/sellside.feedimport.list-v1+json; charset=UTF-8

    [
      {
        "id":           5,
        "url":          "http://ourshop.com/feed.xml",
        "status":       "DONE",
        "dateCreated":  "2016-02-03T15:35:33Z",
        "error":        "",
        "totalCount":   2,
        "okCount":      1,
        "warningCount": 1,
        "errorCount":   0
      },
      {
        "id":           4,
        "url":          "http://ourshop.com/notfound.xml",
        "status":       "REJECTED",
        "dateCreated":  "2016-02-03T15:35:23Z",
        "error":        "HTTP 404 Not Found for: http://ourshop.com/notfound.xml",
        "totalCount":   -1,
        "okCount":      0,
        "warningCount": 0,
        "errorCount":   0
      }
    ]
