.. code-block:: javascript

    1st page is always fetched by applying known query params to the url. The response
    will indicate if there are additional pages to fetch. The nextPageToken field
    contains the value that can be used to fetch the next page.

    GET /ad?limit=1

    200 OK
    Content-Type: application/sellside.ad.list-v5+json; charset=utf-8

    {
        "ads": [
            {...}
        ],
        "count": 22,
        "nextPageToken": "eyJpZCI6MTI3NzA5NTk2Nywic3RyaW5nX3ZhbHVlIjpudWxsLCJpbnQ2NF92YWx1ZSI6MTU1MTE3Nzg1NDcyMH0"
    }

    When fetching subsequent pages, in addition to previously supplied query params,
    it is required to set the additional query param pageToken to the value of the
    nextPageToken received in a previous call.

    GET /ad?limit=1&pageToken=eyJpZCI6MTI3NzA5NTk2Nywic3RyaW5nX3ZhbHVlIjpudWxsLCJpbnQ2NF92YWx1ZSI6MTU1MTE3Nzg1NDcyMH0

    200 OK
    Content-Type: application/sellside.ad.list-v5+json; charset=utf-8

    {
        "ads": [
            {...}
        ],
        "count": 22,
        "nextPageToken": "eyJpZCI6MTI3NzMxOTU1NCwic3RyaW5nX3ZhbHVlIjpudWxsLCJpbnQ2NF92YWx1ZSI6MTU1MTM0MzMzNzE0Nn0"
    }

    When the nextPageToken returned in the response has a null value, it means that there
    are no additional pages to fetch.

    GET /ad?limit=1&pageToken=eyJpZCI6MTI3NzA5NTk2Nywic3RyaW5nX3ZhbHVlIjpudWxsLCJpbnQ2NF92YWx1ZSI6MTU1MTE3Nzg1NDcyMH0

    200 OK
    Content-Type: application/sellside.ad.list-v5+json; charset=utf-8

    {
        "ads": [
            {...}
        ],
        "count": 22,
        "nextPageToken": null
    }