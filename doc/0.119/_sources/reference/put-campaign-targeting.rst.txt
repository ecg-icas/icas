.. index:: PUT /campaign/{id}/targeting

PUT /campaign/{id}/targeting
===============================

.. note::
    **At the moment, we are still in an experimental stage with the campaign targeting options.** Please do not use this field yet, setting it can cause unexpected behaviours. Do shout out to us on Discord if you are interested in using it, we would love to hear.


.. list-table::
 :widths: 20 80

 * - Scope
   - ``api_rw`` or ``console_rw``

 * - Accept
   - ``application/sellside.campaign.targeting-v2+json, application/json``

 * - Content-Type
   - ``application/sellside.campaign.targeting-v2+json, application/json``

Updates the targeting for the specified campaign (see :ref:`Campaign Targeting Object <campaign-targeting-object>` for more). If the ``id`` is invalid, i.e., not a positive integer, the server returns *400 Bad Request.*
Any previous targeting setting on the specified campaign will be overwritten.

Setting targeting on a campaign in a ``DELETED`` state is not allowed.

Examples:
---------

.. include:: ../examples/put-campaign-targeting-example-v2.rst

