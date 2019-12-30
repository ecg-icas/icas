.. code-block:: javascript

    POST /api/sellside/metrics/data
    Content-Type: application/sellside.metrics.data-v1+json
    Accept: application/json

    {
        "timeRanges": [{
            "period": "custom",
            "from": "2020-01-01",
            "to": "2020-01-01"
        }],
        "dimensions": ["am:categoryID"],
	    "metrics": ["am:countDistinctAdID", "am:impressions", "am:clicks", "am:websiteClicks", "am:emails", "am:spent"]
        "filters": [{ // optional, default is all categories
            "field": "am:categoryID",
            "operator": "in",
            "value": [1234, 5678]
        }]
    }
