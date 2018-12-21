.. _Google Analytics: https://developers.google.com/analytics/devguides/reporting/core
.. _Yandex Metrica: https://tech.yandex.com/metrika/

Reporting
===========

The new Reporting API allows you to get statistics about the performance of your ads in a flexible way. It is inspired by
APIs like `Google Analytics`_ and `Yandex Metrica`_ and borrows some terminology from them.
It is possible to create a custom-tailored report structure using concepts like dimensions, metrics, filters, and sorting, in the API query.


Dimensions and Metrics
~~~~~~~~~~~~~~~~~~~~~~~~~
Dimensions and metrics are used for making API requests.
Every report response is made up of them.

Dimensions
****************************
A **dimension** is an attribute of each performance event, and is used for grouping your data. For example, the dimension *Country* indicates
where a click originated from. The *Date* dimension indicates the date when a particular ad was viewed or clicked.
It is also possible to make a report without dimensions; in this case, the total result is calculated.

Metrics
****************************
**Metrics** are numeric values based on quantitative aggregations over dimensions' values; every query requires at least one metric field to be requested.
The metric *Clicks* indicates the total number of clicks. For example, the metric *ViewCTR* indicates the click-through rate for ads.

.. note:: If you are familiar with SQL, you can think of dimensions as columns used for grouping, and metrics as the results returned by aggregate functions. The tables in most reports organize dimension values into rows, and metrics into columns.

To grasp the different views that a report can generate, below is an example of tabular representation typical for analytics reports:


==============  ========  ==================
DIMENSION       METRIC 1    METRIC 2
--------------  --------  ------------------
*Country*       *Clicks*   *ViewCTR*
==============  ========  ==================
Netherlands      1234       0.5678
Spain            987        0.123
France           64523      0.2643
==============  ========  ==================

If we add a secondary dimension, for example *Category*, the resulting view could be:

==============  ==============  =========  ===========
DIMENSION 1       DIMENSION 2    METRIC 1   METRIC 2
--------------  --------------  ---------  -----------
*Country*       *Category*      *Clicks*    *ViewCTR*
==============  ==============  =========  ===========
Netherlands     Bicycles         356        0.5678
Netherlands     Camping Gear     174        0.455
Netherlands     Mobile Phones    546        0.0245
 . . .             . . .         . . .       . . .
Spain           Bicycles         987        0.123
Spain           Camping Gear     5537       0.2311
Spain           Mobile Phones    987        0.123
 . . .             . . .         . . .       . . .
France          Bicycles         12743      0.2357
France          Camping Gear     753        0.1124
France          Bicycles         882        0.3575
==============  ==============  =========  ===========

The dimensions supported by the reporting API have discrete values (like *Netherlands* or *Bicycles*), and the data is split by each such value, over which statistics (like *Clicks* or *Impressions*) are calculated.

Currently Supported Dimensions
********************************************

 * ``am:date`` - the date when the events happened. This is a special dimension (see TODO: aggregate)
 * ``am:adID`` - id of the ad(s)
 * ``am:CPC`` - cpc of the ad(s)
 * ``am:categoryID`` - categoryId of the ad(s)
 * ``am:regionID`` - regionId of the ad(s)


Currently Supported Metrics
********************************************

TODO: hits vs sessions

 * ``am:clicks`` - number of clicks
 * ``am:impressions`` - number of impressions
 * ``am:websiteClicks`` - number of website clicks
 * ``am:emails`` - number of emails
 * ``am:engagements`` - number of engagements (currently ``website clicks + emails``)
 * ``am:viewCTR`` - click through rate (``clicks/impressions``)
 * ``am:websiteCTR`` - website leads from clicks ``(website clicks / clicks)``
 * ``am:spent`` - amount spent (in cents)
 * ``am:engagementCTR`` - engagement click through rate ``(website clicks + emails) / clicks``
 * ``am:avgCPC`` - average CPC ``(total spent / clicks)``

.. note:: *Date* is a special dimension, in that you can specify the granularity of the timeseries breakdown. In other words, data is aggregated over units of time (such as days, weeks, months or years) when calculating metrics over it. See `Time Aggregation`_ for options on granularity.


Filters
~~~~~~~~~~~~~~~~~~~~~~~~~
To request a subset of your data, use filters. For example, you can filter on particular category, or adId. Filters can currently be used on any of the supported dimensions.

Sorting
~~~~~~~
Sort the result based on dimension or metrics values. For example, it is possible to sort in ascending direction on Region, followed by descending direction on Clicks, etc.


Query and Response
~~~~~~~~~~~~~~~~~~

Query
********************
The metrics query should be provided as a JSON object which has these minimum requirements:

* At least one valid entry in the timeRanges `Time Ranges`_ field.

* At least one valid entry in the `Metrics`_ field.

Here is a sample request with all top-level query fields expanded:

.. code-block:: javascript

    GET /api/sellside/metrics/data
    Content-Type: application/sellside.metrics.data-v1+json
    Accept: application/json
.. literalinclude:: examples/metrics-query-v1.json

Response
********************

The response body of the API request is an array of Data (TODO: object describe? with start/end/rows/dimensions/metrics/enrichment) objects. Here is a sample response for the sample request above.

.. literalinclude:: examples/metrics-response-v1.json


Time Ranges
***********

This field is used to specify one ore more distinct time periods to fetch data for, across which all other query parameters will be the same.
Supplying a single range is sufficient for most needs, but the flexibility is provided to ask for multiple at the same time.
Each time range clause is defined as follows:

.. code:: javascript

    {
        "period":	string
        "from":		string
        "to":		string
    }

There are several *predefined* period types at your disposal:

 * ``today``
 * ``yesterday``
 * ``thisWeek``
 * ``lastWeek``
 * ``thisMonth``
 * ``lastMonth``
 * ``thisYear``
 * ``lastYear``

with their obvious meanings.

If you use a predefined period for a particular time range, the *from* and *to* fields of that time range will be ignored.

To use a *custom* period, you need to provide the start (*from*) and end (*to*) date (**both inclusive**) in the following format: `YYYY-MM-DD`.
The end date cannot be before the start one. For example:

.. code:: javascript

    "timeRanges": [
        {
                "period":   "custom",
                "from":     "2017-01-01",
                "to":       "2017-10-22"
        }
    ]


Example with multiple time ranges (mixed custom and predefined)

.. code:: javascript

    "timeRanges": [
        {
            "period":   "thisWeek"
        },
        {
            "period":   "custom"
            "from":     "2017-01-08",
            "to":       "2017-01-15"
        }
    ]


.. literalinclude:: examples/metrics-response-v1.json

Time Aggregation
****************

HERE BE DRAGONS

Examples
~~~~~~~~

HERE BE MORE DRAGONS
