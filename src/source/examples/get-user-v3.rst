.. code-block:: javascript

    GET /user
    Accept: application/sellside.user-v3+json, application/json

    200 OK HTTP/1.1
    Content-Type: application/sellside.user-v3+json; charset=UTF-8
    {
        "id": 123,
        "emailAddress": "someuser@ebay.com",
        "sellerName": "Some User",
        "phoneNumber": "0612345678",
        "options": {
            "feed": true,
            "vanityUrl": false
        },
        "locations": [
            {
                "houseNumber": "123",
                "streetName": "Some street",
                "city": "Some city",
                "country": "Some country",
                "postalCode": "1432AB",
                "phoneNumber": "0612345678"
            }
        ],
        "hasAds": true
    }
