.. code-block:: javascript

    GET /api/sellside/report/detail
    Accept: application/sellside.report.detail.list-v1+json, application/json

    200 OK
    Content-Type: application/sellside.report.detail.list-v1+json; charset=utf-8

    [
        {
            "id": "c4e91116-34f7-4bbe-959f-12b7a03157ed",
            "dateCreated": "2015-04-16T10:46:41Z",
            "startDate": "2015-04-03T22:00:00Z",
            "endDate": "2015-04-07T22:00:00Z",
            "includeDeleted": true,
            "count": 123
        },
        {
            "id": "d5d4a002-0a82-46f8-8246-9af425490c22",
            "dateCreated": "2015-04-16T10:46:29Z",
            "startDate": "2015-04-03T22:00:00Z",
            "endDate": "2015-04-07T22:00:00Z",
            "includeDeleted": true,
            "count": 16
        },
        {
            "id": "32d031e8-fff4-44df-9f82-72b38618a9ca",
            "dateCreated": "2015-04-09T12:44:47Z",
            "startDate": "2015-02-28T23:00:00Z",
            "endDate": "2015-03-07T23:00:00Z",
            "includeDeleted": false,
            "count": 0
        }
    ]
