.. code-block:: javascript

  GET /api/sellside/campaign/byVendor/my-christmas-campaign-3A
  Accept: application/sellside.campaign-v2+json, application/json

  200 OK HTTP/1.1
  Content-Type: application/sellside.campaign-v2+json; charset=utf-8

  {
    "id": 1234,
    "title": "My christmas campaign",
    "dateCreated": "2016-02-03T15:35:33Z",
    "dateLastUpdated": "2016-02-03T15:35:33Z",
    "status": "ACTIVE",
    "vendorId: "my-christmas-campaign-3A"
  }
