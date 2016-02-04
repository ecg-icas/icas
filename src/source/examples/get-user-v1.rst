.. code-block:: javascript

    GET /user
    Accept: application/sellside.user-v1+json, application/json

    200 OK HTTP/1.1
    Content-Type: application/sellside.user-v1+json; charset=UTF-8

    {
        "id":           123,
        "emailAddress": "someuser@ebay.com",
        "sellerName":   "Some User",
        "phoneNumber":  "0612345678",
        "options": {
            "feed": true,
            "vanityUrl": true
        }
    }
