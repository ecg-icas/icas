.. code-block:: javascript

    GET /ad[?limit=limit][&nextPageToken=token][&titleKeywords=titleKeywords][&status=Status][&orderBy=orderBy][&changedSince=timestamp]
    Accept: application/sellside.ad.list-v5+json, application/json

    200 OK
    Content-Type: application/sellside.ad.list-v5+json; charset=utf-8

    {
        "ads": [
            {
                "id": 5,
                "title": "Brother Fax voor 99,99",
                "description": "\u003cSTRONG\u003eNU extra voordelig op ourshop.com.\u003c/STRONG\u003e Fax nu voor slechts \u003cSTRONG\u003e99,99!\u003c/STRONG\u003e",
                "category_id": 826,
                "price_type": "FIXED_PRICE",
                "price": 9999,
                "salutation": "COMPANY",
                "seller_name": "My Shop",
                "phone_number": "0207894561",
                "allow_contact_by_email": true,
                "status": "ACTIVE",
                "postcode": "1097DN",
                "dateCreated": "2020-06-15T13:23:33Z",
                "dateLastUpdated": "2020-06-15T13:23:33Z",
                "vendorId": "myshop-5",
                "attributes": [],
                "images": [],
                "shippingOptions": [],
                "links": {
                    "url": "http://www.ourshop.com/index.php?param1=value1\u0026amp;param2=value2\u0026amp;param3=value3",
                    "displayUrl": "www.ourshop.com/Faxes",
                    "self": "/api/sellside/ad/5",
                    "category": "/api/sellside/category/826"
                }
            },
            {
                "id": 6,
                "title": "Sister Notebook voor 99,99",
                "description": "\u003cSTRONG\u003eNU extra voordelig op ourshop.com.\u003c/STRONG\u003e Fax nu voor slechts \u003cSTRONG\u003e99,99!\u003c/STRONG\u003e",
                "category_id": 826,
                "price_type": "FIXED_PRICE",
                "price": 9999,
                "salutation": "COMPANY",
                "seller_name": "My Shop",
                "phone_number": "0207894561",
                "allow_contact_by_email": true,
                "status": "ACTIVE",
                "postcode": "1097DN",
                "dateCreated": "2020-06-15T13:23:40Z",
                "dateLastUpdated": "2020-06-15T13:23:40Z",
                "vendorId": "myshop-6",
                "attributes": [],
                "images": [],
                "shippingOptions": [],
                "links": {
                    "url": "http://www.ourshop.com/index.php?param1=value1\u0026amp;param2=value2\u0026amp;param3=value3",
                    "displayUrl": "www.ourshop.com/Faxes",
                    "self": "/api/sellside/ad/6",
                    "category": "/api/sellside/category/826"
                }
            }
        ],
        "count": 9,
        "next_page_token": "eyJpZCI6Nywic3RyaW5nX3ZhbHVlIjpudWxsLCJpbnQ2NF92YWx1ZSI6MTU5MjIyNzQzOTI5OX0"
    }
