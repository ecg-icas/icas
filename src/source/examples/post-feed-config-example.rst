.. code-block:: javascript

    POST /api/sellside/feed/config
    Accept: application/sellside.feedconfig-v1+json, application/json
    Content-Type: application/sellside.feedconfig-v1+json

    {
        "enabled": true,
        "feedUrl": "http://www.ourshop.com/feed.xml"
    }