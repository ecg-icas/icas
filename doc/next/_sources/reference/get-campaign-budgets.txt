.. index:: GET /campaign/{id}/budgets

GET /campaign/{id}/budgets
============================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.campaign.budgets-v2+json, application/json``

Returns a :ref:`Campaign Budgets Object <campaign-budgets-object>` for the specified campaign. If the ``id`` is invalid, i.e., not a positive integer, the server returns *400 Bad Request.*

If the campaign is in DELETED status, `404 Not Found` is returned.

Example:
--------

.. include:: ../examples/get-campaign-budgets-example-v2.rst
