To understand the concept of dimensions and metrics, some examples of request and response are provided below, gradually increasing in complexity. In addition, a "tabular" view of the response is provided; in our experience it makes it easier to grasp these concepts.

Example 1:
************************************************************************

Get all clicks and impressions for category ``1234`` for the previous week:


.. code:: javascript


    POST /api/sellside/metrics/data
    Content-Type: application/sellside.metrics.data-v2+json
    Accept: application/json
    {
        "timeRanges": [{
            "period": "lastWeek"
        }],
        "dimensions": [],
        "metrics": ["am:clicks", "am:impressions"],
        "filters": [{
            "field": "am:categoryID",
            "operator": "in",
            "value": [1234]
        }]
    }


.. code:: javascript

    {
        "data": [{
            "rows": [{
                "dimensions": [],
                "metrics": [1483, 36623] // 1483 clicks, 36623 impressions
            }],
        "count": 1
        }]
    }


==========   ===================
am:clicks     am:impressions
==========   ===================
1483          36623
==========   ===================

Example 2:
************************************************************************

Get all clicks and impressions for categories ``1234`` and ``5678`` for the previous week, but split performance metrics per category:


.. code:: javascript


    POST /api/sellside/metrics/data
    Content-Type: application/sellside.metrics.data-v2+json
    Accept: application/json
    {
        "timeRanges": [{
            "period": "lastWeek"
        }],
        "dimensions": ["am:categoryID"],
        "metrics": ["am:clicks", "am:impressions"],
        "filters": [{
            "field": "am:categoryID",
            "operator": "in",
            "value": [1234, 5678]
        }]
    }


.. code:: javascript

    {
        "data": [{
            "rows": [{
                "dimensions": ["1234"],
                "metrics": [200, 400] // 200 clicks, 400 impressions for category "1234"
            },
            {
                "dimensions": ["5678"],
                "metrics": [300, 400]
            }],
        "count": 2
        }]
    }


===============   ==========   ===================
 am:categoryID    am:clicks     am:impressions
===============   ==========   ===================
    1234           200          400
    5678           300          400
===============   ==========   ===================


Example 3:
************************************************************************

Get all clicks and impressions for categories ``1234`` and ``5678`` for the previous week, but split performance metrics per day and category. In addition, sort by date in ascending direction:

.. code:: javascript


    POST /api/sellside/metrics/data
    Content-Type: application/sellside.metrics.data-v2+json
    Accept: application/json
    {
        "timeRanges": [{
            "period": "lastWeek"
        }],
        "dimensions": ["am:date", "am:categoryID"],
        "metrics": ["am:clicks", "am:impressions"],
        "filters": [{
            "field": "am:categoryID",
            "operator": "in",
            "value": [1234, 5678]
        }],
        "sorts":[
        {
            "field":"am:date",
            "direction":"asc"
        }],
    }


.. code:: javascript

    {
        "data": [{
            "rows": [{
                "dimensions": ["2018-12-08 00:00:00", "1234"],
                "metrics": [11, 12]
            },
            {
                "dimensions": ["2018-12-08 00:00:00", "5678"],
                "metrics": [9, 20]
            },
            {
                "dimensions": ["2018-12-09 00:00:00", "1234"],
                "metrics": [34, 67]
            },
                        {
                "dimensions": ["2018-12-09 00:00:00", "5678"],
                "metrics": [19, 20]
            },
            ...
            {
                "dimensions": ["2018-12-14 00:00:00", "1234"],
                "metrics": [12, 90]
            },
            {
                "dimensions": ["2018-12-14 00:00:00", "5678"],
                "metrics": [43, 76]
            }],
        "count": 54
        }]
    }


=====================   ===============   ==========   ===================
  am:date                 am:categoryID    am:clicks     am:impressions
=====================   ===============   ==========   ===================
 2018-12-08 00:00:00        1234           11           12
 2018-12-08 00:00:00        5678           9            20
 2018-12-09 00:00:00        1234           34           67
 2018-12-09 00:00:00        5678           19           20
 ...
 2018-12-14 00:00:00        1234           12           90
 2018-12-14 00:00:00        5678           43           76
=====================   ===============   ==========   ===================


Example 4:
************************************************************************

Get all clicks, and average CPC for categories ``1234`` and ``5678`` for the previous week, but split performance metrics per ad ID. In addition, enrich the response rows with current ad title and vendorID. Limit to 3 results:


.. code:: javascript

    POST /api/sellside/metrics/data
    Content-Type: application/sellside.metrics.data-v2+json
    Accept: application/json
    {
        "timeRanges": [{
            "period": "lastWeek"
        }],
        "dimensions": ["am:adID"],
        "metrics": ["am:clicks", "am:avgBidMicros"],
        "filters": [{
                "field": "am:categoryID",
                "operator": "in",
                "value": [1234, 5678]
        }],
        "enrichment":["am:currentAdTitle", "am:currentAdVendorID"]
        "limit": 3
    }



.. code:: javascript

    {
        "data": [{
            "rows": [{
                "dimensions": ["11111"],
                "metrics": [11, 45000.0],
                "enrichment": [
                    "Ad title #11111",
                    "vendor11111"
                ]
            },
            {
                "dimensions": ["33333"],
                "metrics": [9, 30000.0],
                "enrichment": [
                    "Ad title #33333",
                    "vendor33333"
                ]
            },
            {
                "dimensions": ["22222"],
                "metrics": [34,  20003.0],
                    "enrichment": [
                    "Ad title #33333",
                    "vendor33333"
                ]
            }],
        "count": 3
        }]
    }


=====================   ==============   ===================  ====================   =====================
  am:adID                 am:clicks       am:avgBidMicros      am:currentAdTitle       am:currentAdVendorID
=====================   ==============   ===================  ====================   =====================
11111                       11            45000.0              Ad title #11111         vendor11111
33333                       9             30000.0              Ad title #33333         vendor33333
22222                       34            23000.0              Ad title #22222         vendor22222
=====================   ==============   ===================  ====================   =====================

Final remarks:
************************************************************************
 * In the :ref:`SQL note <SQL-note>`, the enrichment fields can be seen as a left outer join operation.
 * The reporting numbers may slightly differ (±0.005%) from the final billing values, due to the nature of the system where we store the reporting data.
 * The API **does not allow to filter on the current status of ads**, which means the reporting numbers apply for **all** ads, including those that have been deleted in the meantime. Depending on API clients feedback, we might revisit the API and add support for such filtering in the future.
