.. code-block:: javascript

    GET /api/sellside/feed/import/123/detail/vndr
    Accept: application/sellside.feedimportdetail-v1+json; application/json

    200 OK
    Content-Type: application/sellside.feedimportdetail-v1+json; charset=UTF-8

    {
      "vendorID":    "vndr",
      "errors":      [
        "title \"\" too short, minimum is 1 characters"
      ],
      "warnings":[
        "total budget defaults to 200000000"
      ],
      "dateCreated": "2016-02-03T14:59:02Z"
    }
