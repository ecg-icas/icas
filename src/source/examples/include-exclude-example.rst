Here's an example of the ``_include`` parameter used while calling `GET /ad <https://ecg-icas.github.io/icas/openapi/index.html#/Ads/getListOfAdsWithFilters>`_.
The normal response has the following shape:

.. code-block:: javascript

    {
      "ads": [
        {
          "id": 42,
          "title": "Brother Fax voor 99,99",
          "status": "ACTIVE",
          ....
          <many more fields>
          ....
        },
        {
        "id": 46,
        "title": "Brother Printer voor 69,99",
        "status": "ACTIVE",
        ....
        <many more fields>
        ....
        },
        ....
        <many more ads>
        ...
      ],
      "count": 4241,
      "nextPageToken": "eyJpZCI6MTAwMTgzMTc1MCwic3RyaW5nX3ZhbHVlIjpudWxsLCJpbnQ2NF92YWx1ZSI6MTM0MDIxNzg1OTc5MH0"
    }

If you want to paginate through all ads and only get the `id` & `status` then you should call
`GET /api/sellside/ad?_include=ads,id,status,nextPageToken` to get the following result:

.. code-block:: javascript

    {
      "ads": [
        {
            "id": 42,
            "status": "ACTIVE",
        },
        {
            "id": 46,
            "status": "ACTIVE",
        },
        ....
        <many more ads with only id & status>
        ...
      ],
      "nextPageToken": "eyJpZCI6MTAwMTgzMTc1MCwic3RyaW5nX3ZhbHVlIjpudWxsLCJpbnQ2NF92YWx1ZSI6MTM0MDIxNzg1OTc5MH0"
    }

and the next page, using the `nextPageToken` would become `GET /api/sellside/ad?_include=ads,id,status,nextPageToken?pageToken=eyJpZCI6MTAwMTgzMTc1MCwic3RyaW5nX3ZhbHVlIjpudWxsLCJpbnQ2NF92YWx1ZSI6MTM0MDIxNzg1OTc5MH0`