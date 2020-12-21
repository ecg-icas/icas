.. index:: PUT /campaign/{id}/status/{status}
.. _put_campaign_status:

PUT /campaign/{id}/status/{status}
===================================

.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.campaign-v2+json``


Updates the status for the specified campaign. Can be one of the user-controlled status values described in :ref:`User Controlled States <user-controlled-states>`. If successful, the server responds with `HTTP 200` and returns the full updated campaign payload.

.. include:: ../examples/put-campaign-status-v2-example.rst
