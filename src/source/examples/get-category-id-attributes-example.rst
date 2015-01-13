.. code-block:: javascript

    GET /category/4/attributes
    Accept: application/sellside.attribute.list-v1+json

    [
        {
            "key": "Delivery",
            "label": "Levering",
            "locale" : "nl",
            "type" : "STRING",
            "values" : ["Ophalen", "Verzenden", "Ophalen of Verzenden"]
        },
        {
            "key": "Properties",
            "label": "Eigenschappen",
            "locale" : "nl",
            "type" : "LIST",
            "values" : ["Met bandje", "Met ketting", "Verguld"]
        },
        {
            "key": "Motorinhoud",
            "label": "Motorinhoud",
            "locale" : "nl",
            "type" : "NUMBER",
            "minValue" : 1,
            "maxValue" : 8500
        },
        ...
    ]