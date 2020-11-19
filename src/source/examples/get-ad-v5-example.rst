.. code-block:: javascript

    GET /ad[?limit=limit][&nextPageToken=token][&titleKeywords=titleKeywords][&status=Status][&orderBy=orderBy][&changedSince=timestamp]
    Accept: application/sellside.ad.list-v5+json, application/json

    200 OK
    Content-Type: application/sellside.ad.list-v5+json; charset=utf-8

    {
        "ads": [
            {
                "id": 67233610,
                "title": "Brother Fax voor 99,99",
                "description": "\u003cSTRONG\u003eNU extra voordelig op ourshop.com.\u003c/STRONG\u003e Fax nu voor slechts \u003cSTRONG\u003e99,99!\u003c/STRONG\u003e",
                "categoryId": 2,
                "priceType": "FIXED_PRICE",
                "price": 9999,
                "salutation": "COMPANY",
                "sellerName": "My Shop",
                "phoneNumber": "0207894561",
                "allowContactByEmail": true,
                "status": "ACTIVE",
                "postcode": "1000AA",
                "dateCreated": "2018-12-17T13:17:34Z",
                "dateLastUpdated": "2019-11-18T13:18:54Z",
                "images": [
                    {
                        "status": "OK",
                        "src": "https://i.ebayimg.com/00/s/MTAyNFgxMDI0/z/whWZppA/$_86.JPG",
                        "dateLastUpdated": "2019-11-18T13:18:57Z",
                        "links": {
                            "1024x1024": "//i.ebayimg.com/00/s/MTAyNFgxMDI0/z/whWZppA/$_86.JPG",
                            "147x147": "//i.ebayimg.com/00/s/MTAyNFgxMDI0/z/whWZppA/$_82.JPG",
                            "358x358": "//i.ebayimg.com/00/s/MTAyNFgxMDI0/z/whWZppA/$_83.JPG",
                            "64x64": "//i.ebayimg.com/00/s/MTAyNFgxMDI0/z/whWZppA/$_14.JPG",
                            "726x726": "//i.ebayimg.com/00/s/MTAyNFgxMDI0/z/whWZppA/$_85.JPG"
                        }
                    }
                ],
                "shippingOptions": [
                    {
                        "type": "PICKUP",
                        "pickupLocation": "1000AA"
                    }
                ],
                "links": {
                    "url": "http://www.ourshop.com",
                    "displayUrl": "http://www.ourshop.com",
                    "self": "/api/sellside/ad/67233610",
                    "category": "/api/sellside/category/2"
                },
                "regionId": null,
                "externalId": "myshop-1"
            }
        ],
        "count": 22,
        "nextPageToken": "eyJpZCI6MTI3NzA5NTk2Nywic3RyaW5nX3ZhbHVlIjpudWxsLCJpbnQ2NF92YWx1ZSI6MTU1MTE3Nzg1NDcyMH0"
    }
