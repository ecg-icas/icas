.. code-block:: console

    GET /api/sellside/metrics/ads?startDate=2018-01-01&endDate=2018-05-01&query=Interesting
    Accept: text/csv
    Accept-Language: nl_NL, fr_NL;q=0.5

    HTTP/1.1 200 OK
    Content-Type: text/csv
    Content-Language: nl-NL
    Content-Disposition: attachment; filename=mp-report-1-20180202-144320.csv
    Datum (geaggregeerde),Advertentie nummer,Groep,Rubriek,,Advertentietitel,Start,Eind,CPC (EUR),Totaal besteed (EUR),Clicks,Impressies,CTR (%),URL Clicks,E-mails,Engagement CTR (%),Vendor ID,Region
    2018-02-02,7,Cd's en Dvd's,Cd's | Country en Western,,"Interesting title, what about ""quotes""",2018-02-02 11:48:52,,0.1500000000,0.3000000000,2,4,50.0000000000,0,0,0.0000000000,someVendor7,Utrecht
    2018-02-03,8,Cd's en Dvd's,Cd's | Country en Western,,Interesting CD with country music,2018-02-02 11:48:52,,0.1500000000,0.3000000000,2,4,50.0000000000,0,0,0.0000000000,someVendor8,Amsterdam


.. code-block:: console

    GET /api/sellside/metrics/ads?startDate=2018-01-01&endDate=2018-05-01&query=Interesting&aggregate=monthly
    Accept: text/csv

    HTTP/1.1 200 OK
    Content-Type: text/csv
    Content-Disposition: attachment; filename=mp-report-1-20180202-144330.csv
    Datum (geaggregeerde),Advertentie nummer,Groep,Rubriek,,Advertentietitel,Start,Eind,CPC (EUR),Totaal besteed (EUR),Clicks,Impressies,CTR (%),URL Clicks,E-mails,Engagement CTR (%),Vendor ID,Region
    2018-02,7,Cd's en Dvd's,Cd's | Country en Western,,"Interesting title, what about ""quotes""",2018-02-02 11:48:52,,0.1500000000,0.3000000000,20,40,50.0000000000,0,0,0.0000000000,someVendor7,Utrecht
    2018-02,8,Cd's en Dvd's,Cd's | Country en Western,,Interesting CD with country music,2018-02-02 11:48:52,,0.1500000000,0.3000000000,20,40,50.0000000000,0,0,0.0000000000,someVendor8,Amsterdam


.. code-block:: console

    GET /api/sellside/metrics/ads?startDate=2018-01-01&endDate=2018-05-01&query=Interesting&aggregate=yearly&fields=date,adID,clicks,spent
    Accept: text/csv

    HTTP/1.1 200 OK
    Content-Type: text/csv
    Content-Disposition: attachment; filename=mp-report-1-20180202-144340.csv
    Datum (geaggregeerde),Advertentie nummer,Totaal besteed (EUR),Clicks
    2018,7,0.3000000000,20
    2018,8,0.1500000000,0.3000000000


Errors
========================
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


