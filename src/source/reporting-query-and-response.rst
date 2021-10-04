
Query
************************************
The metrics query should be provided as a JSON object of type `Metrics Request`_, which has these minimum requirements:

* At least one valid entry in the  :ref:`Time Ranges <time-ranges>` field.

* At least one valid entry in the :ref:`Metrics <metrics>` field.

Metrics Request
######################################################

The data model of the request has the following structure:

.. code-block:: javascript

    {
        "timeRanges": [<timeRange>, ...],
        "aggregate": <string>,
        "dimensions": [<string>, ...],
        "metrics": [<string>, ...],
        "sorts": [<sort>, ...],
        "filters": [<filter>, ...],
        "enrichment": [<string>, ...],
        "limit": <integer>,
        "offset": <integer>,
        "searchPhrase": <string>
    }


==================  ======================================
Parameter           Description
==================  ======================================
``timeRanges``      Array of :ref:`Time Ranges <time-ranges>` objects, separated by commas
``aggregate``       One of :ref:`Time Aggregation <time-aggregation>` string values
``dimensions``      Array of dimensions, separated by commas
``metrics``         Array of metrics, separated by commas. At least one element is mandatory
``sorts``           Array of :ref:`Sort <Sorts>`  objects, separated by commas
``filters``         Array of :ref:`Filters <filters>` objects, separated by commas
``enrichment``      Array of ad enrichment fields, separated by commas
``limit``           Number of elements in the response, per time range. By default there is no limit
``offset``          Index of first row of the requested data (per time range), beginning with 0
``searchPhrase``    String to match against an ad title
==================  ======================================


Metrics Response
######################################################

The data model of the response has the following structure:

.. code-block:: javascript


    {
        "data": [
            {
                "rows": [
                    {
                        "dimensions": [<string>, ... ],
                        "metrics": [ <number>, ...]
                        "enrichment": [<string>, ...]
                    }
                , ...],
            "count": <integer>
            }
        ]
    }


================  ======================================
Parameter          Description
================  ======================================
``rows``           Array of ``dimensions``, ``metrics`` and ``enrichment`` values. Each element is one row of a response
``dimensions``     Array of dimension values for this row, in string format
``metrics``        Array of metric values for this row, in number format
``enrichment``     Array of enrichment values for this row, in string format. Valid only if ``am:adID`` is in the requested dimensions
``count``          Actual number of rows returned
================  ======================================

The ``data`` field contains an array of objects, one for each of the requested :ref:`Time Ranges <time-ranges>`. It is **important to remember** that the order in which the ``metrics``, ``dimensions``, and ``enrichment`` fields are requested is the same order in which they are listed in the response. The order of the objects in the `rows` array is not guaranteed to be deterministic unless explicit `Sorting <Sorts>` is used.
