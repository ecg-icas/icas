.. code-block:: javascript

    POST /image
    Accept: application/sellside.image.list-v1+json, application/json
    Content-Type: multipart/form-data; boundary=a1b8

    --a1b8
    Content-Disposition: form-data; name="image1"; filename="logo.png"
    Content-Type: application/octet-stream

    ...image bytes...
    --a1b8

    200 OK
    Content-Type: application/sellside.image.list-v1+json; charset=utf-8

    {
        "image1": "https://localhost/api/sellside/image/9beac3db90c27aa8476cb880a362ceba/b2c11184b33bdd3e12a1f46152d37a89.jpg"
    }