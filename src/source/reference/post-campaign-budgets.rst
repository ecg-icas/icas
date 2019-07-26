.. index:: POST /campaign/{id}/budgets

POST /campaign/{id}/budgets
============================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.campaign-budgets-v2+json, application/json``

 * - Content-Type
   - ``application/sellside.campaign-budgets-v2+json, application/json``

Updates the budgets limits for the specified campaign (see :ref:`Campaign Budgets Object <campaign-budgets-object>` for more). If the ``id`` is invalid, i.e., not a positive integer, the server returns *400 Bad Request.*
Any previous budgets limits on the specified campaign will be overwritten. Any budget type which is not included in the payload, will be set to **-1 (Unlimited**).

Examples:
---------

.. include:: ../examples/post-campaign-budgets-example-v2.rst

The ``spent`` values in each budget type are **read-only**.

