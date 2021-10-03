.. index:: POST /metrics/data
.. _post_metrics_data:

POST /metrics/data
==================

:ref:`post_metrics_data_v2` | :ref:`post_metrics_data_v1`


.. _post_metrics_data_v2:

POST /metrics/data V2
---------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/json``
 * - Content-Type
   - ``application/sellside.metrics.data-v2+json``

This URL returns the requested reporting metrics in a format described in the new :ref:`metrics_reporting_v2` API.

Query and Response
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. include:: /reporting-query-and-response-v2.rst

.. _examples_post_metrics_data_v2:

Examples
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

..  include:: /reporting-examples-v2.rst


Errors
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

..  include:: /reporting-errors.rst



.. _post_metrics_data_v1:

POST /metrics/data V1
---------------------

.. list-table::
 :widths: 20 80

 * - Scope
   - ``console_ro`` or ``api_ro``

 * - Accept
   - ``application/json``
 * - Content-Type
   - ``application/sellside.metrics.data-v1+json``

This URL returns the requested reporting metrics in a format described in the new :ref:`metrics_reporting_v1` API.

Query and Response
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. include:: /reporting-query-and-response-v1.rst

.. _examples_post_metrics_data_v1:

Examples
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

..  include:: /reporting-examples-v1.rst


Errors
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

..  include:: /reporting-errors.rst
