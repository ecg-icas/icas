.. code-block:: console

    GET /api/sellside/metrics/ads?startDate=2018-01-01&endDate=2018-05-01&query=Interesting
    Accept: application/json

    HTTP/1.1 415 Unsupported Media Type
    [
        {
            "code": 2007,
            "text": "unsupported format",
            "msg": "unsupported media type",
            "field": "",
            "arg": ""
        }
    ]


.. code-block:: console

    GET /api/sellside/metrics/ads?startDate=2018-01-01
    Accept: application/vnd.ms-excel

    HTTP/1.1 400 Bad Request
    [
        {
            "code": 2000,
            "text": "missing argument",
            "msg": "The field 'endDate' was missing",
            "field": "endDate",
            "arg": ""
        }
    ]


.. code-block:: console

    GET /api/sellside/metrics/ads?startDate=2018-07-01&endDate=2018-05-01

    HTTP/1.1 400 Bad Request
    [
        {
            "code": 2002,
            "text": "out of range",
            "msg": "The value of the field 'endDate' was out of range (< startDate)",
            "field": "endDate",
            "arg": "< startDate"
        }
    ]
