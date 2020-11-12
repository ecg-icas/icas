.. code-block:: javascript

    PUT /api/sellside/campaign/123/vendorId/vendor123
    Accept: application/sellside.campaign.vendor.id-v2+json; charset=utf-8

    HTTP 200 OK
    Content-Type: application/sellside.campaign.vendor.id-v2+json; charset=utf-8


    PUT /api/sellside/campaign/123/vendorId/vendor1234
    Accept: application/sellside.campaign.vendor.id-v2+json; charset=utf-8

    HTTP 400 Bad Request
    Content-Type: aapplication/json; charset=utf-8
    [
        {
            "code": 2024,
            "text": "vendorId change not allowed",
            "msg": "The field 'vendorId' contains a value (vendor1234) that is different than what was previously set (vendor123)",
            "field": "vendorId",
            "arg": "vendor1234"
        }
    ]
