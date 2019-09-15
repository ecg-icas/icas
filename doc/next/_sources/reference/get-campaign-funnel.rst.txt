.. index:: GET /campaign/{id}/funnel

GET /campaign/{id}/funnel
============================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_ro`` or ``console_ro``

 * - Accept
   - ``application/sellside.campaign-targeting-v2+json, application/json``

Returns a :ref:`Campaign Funnel Object <campaign-funnel-object>` for the specified campaign. If the ``id`` is invalid, i.e., not a positive integer, the server returns *400 Bad Request.*
The funnel estimates the daily performance of the specified campaign, based on the the budgets, targeting settings and the currently-active ads in the campaign.


.. _campaign-funnel-object:

.. include:: ../examples/campaign-funnel-object.rst


Example:
--------

.. include:: ../examples/get-campaign-funnel-example-v2.rst

TODO: figure out if we want to keep the current API and expose it as it is. We should maybe wait until CDATA...


