.. code-block:: javascript

    GET /budget/seller
    Accept: application/sellside.seller.budget-v1+json, application/json

    200 OK HTTP/1.1
    Content-Type: application/sellside.seller.budget-v1+json; charset=UTF-8

    {
        "amount": 123,
        "adsPaused": false
    }

and in case there is no seller-level budget set up for the user:

.. code-block:: javascript

    GET /budget/seller
    Accept: application/sellside.seller.budget-v1+json

    {}
