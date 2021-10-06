.. index:: POST /metrics/data
.. _post_metrics_data:

POST /metrics/data
=======================

V2
~~~
.. list-table::
 :widths: 20 80

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/json``
 * - Content-Type
   - ``application/sellside.metrics.data-v2+json``

Version 2 is replacing fields that are showing values in cents with their corresponding values in micros. One cent equals to 10000 micros. This allows more granular setting of bid values which was limited down to the size of one cent. This version also introduces billed vs bid values differentiation which is expressed by BidMicros and BilledMicros. 

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

This URL returns the requested reporting metrics in a format described in the new :ref:`metrics_reporting` API.

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
