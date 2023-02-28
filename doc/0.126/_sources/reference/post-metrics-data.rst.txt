.. index:: POST /metrics/data
.. _post_metrics_data:


POST /metrics/data
=======================

.. include:: ../bidding-micros.rst

V2
~~~

V2 removes ``am:cpc`` from dimensions. It replaces ``am:spent``, ``am:avgCPC``, ``am:eCPC``, ``am:sessionECPC`` metrics with their corresponding ``am:spentMicros``, ``am:avgBidMicros``, ``am:eSpentMicros``, ``am:sessionESpentMicros``. It replaces ``am:currentAdCPC`` enrichment with ``am:currentAdBidMicros``.


.. list-table::
 :widths: 20 80

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/json``
 * - Content-Type
   - ``application/sellside.metrics.data-v2+json``

This URL returns the requested reporting metrics in a format described in the new :ref:`metrics_reporting` API.

V1
~~~
.. list-table::
 :widths: 20 80

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/json``
 * - Content-Type
   - ``application/sellside.metrics.data-v1+json``


Query and Response
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. include:: /reporting-query-and-response.rst

.. _examples_post_metrics_data:

Examples
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

..  include:: /reporting-examples.rst


Errors
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

..  include:: /reporting-errors.rst
